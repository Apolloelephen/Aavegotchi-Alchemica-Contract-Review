
# Contract Review of the Aavegotchi Alchemica Facet

## The Aavegotchi game

![Aavegotchi!](https://pbs.twimg.com/profile_banners/1280538599557984256/1688828972/1500x500 "Aavegotchi")

Aavegotchis are unique digital collectibles that are stored on the Polygon blockchain. Each Aavegotchi can be personalized with different accessories, like hats and glasses.

The objective of The Game is to collect alchemica, which is available in four varieties: FOMO, KEK, ALPHA, and FUD. Players can obtain alchemica through channeling, farming, and scavenging.

Here are some details on how alchemica is channeled:

- Aavegotchis can channel alchemica by visiting altars and clicking the "Channel Alchemica" action button, which rewards them with alchemica based on their kinship level. Higher kinship levels result in more alchemica received. Some of the alchemica spills onto nearby land, allowing players to scavenge it before others. The spillover rate determines how much alchemica is distributed to the Aavegotchis and how much spills over. Higher-level altars have lower spillover rates and shorter cooldown times between channeling, adding a strategic element for players to consider when choosing where to channel alchemica

- Guilds play a crucial role in channeling within the Gotchi universe, offering Gotchi Lodges of varying sizes where players can decorate with furniture and showcase NFTs. To join a guild, players require a guild crest, an NFT that acts as a key provided by guild owners to members. Channeling with a guild provides numerous benefits, such as a social gaming experience and increased alchemica rewards. The quantity and rarity of Aavegotchis within the guild directly impact the amount of alchemica received.

- Wearable crests for guilds can be acquired through bid-to-earn auctions utilizing glitter tokens. Glitter tokens hold utility and are distributed over a 30-year period, with 10% released in the first year and halving every four years. Players have the opportunity to earn glitter by providing liquidity to the Aavegotchi decentralized exchange (GAX) using ghost FUD, FOMO, KEK, and ALPHA tokens. The accumulation of glitter tokens enables players to expedite installation build times, with each unit of glitter reducing the build time by one block.

- The GotchiVerse Bible emphasizes the importance of wearable abilities for Gotchis in enhancing their skills and abilities in the GotchiVerse. It teaches that choosing the right abilities and constantly upgrading them is crucial for success in battles and challenges. Gotchis are encouraged to seek out powerful abilities, upgrade them regularly, and use wisdom in selecting the right ones for their individual needs. Ultimately, wearable abilities are seen as essential tools for achieving greatness in the GotchiVerse.

This information sheds light on how alchemical channeling, guilds, glitter tokens, and wearables operate in the Aavegotchi game.

#### Link to Contract

[AlchemicaFacet.sol](https://github.com/aavegotchi/aavegotchi-realm-diamond/blob/master/contracts/RealmDiamond/facets/AlchemicaFacet.sol)

## Contract Review 

#### Imports and Constants

- The contract imports several libraries and interfaces, including `AppStorage`, `RealmFacet`, `LibRealm`, `LibMeta`, `VRFCoordinatorV2Interface`, `LibAlchemica`, `LibSignature`, and `IERC20Extended`. These are used for various functionalities such as storage management, realm-related operations, Chainlink VRF for randomness, and ERC20 token interactions.
`bp` is a constant representing 100 ether, used for calculations related to alchemica distribution or rates.

#### Contract Declaration

- The contract `AlchemicaFacet` inherits from `Modifiers`, which presumably contains modifier functions for access control and other common checks.

#### Events

- Several events are declared to log significant actions within the contract, such as starting surveying, channeling alchemica, exiting alchemica, progressing surveying rounds, and transferring tokens to gotchis.

#### Error

- An error `ERC20TransferFailed` is defined to handle failures in ERC20 token transfers.

#### Functions

- `isSurveying`: Checks if a parcel is currently being surveyed.

- `startSurveying`: Allows the owner of a parcel to start surveying. It includes checks to ensure the parcel is not already surveying and that the parcel has an altar equipped.

- `drawRandomNumbers`: Requests random numbers from Chainlink VRF for surveying purposes.

- `getAlchemicaAddresses`: Returns the addresses of the alchemica tokens.

- `getTotalAlchemicas`: Returns the total alchemica available across all parcels.

- `getRealmAlchemica`: Returns the remaining alchemica in a specific parcel.

- `getParcelCurrentRound`: Returns the current round of surveying for a parcel.

- `progressSurveyingRound`: Increments the surveying round, likely to progress the game's state.

- `getRoundAlchemica`: Returns the alchemica gathered in a specific round of a parcel.

- `getRoundBaseAlchemica`: Returns the base alchemica gathered in a specific round of a parcel.

- `setVars`: Sets various important state variables, including alchemica amounts, boost multipliers, portal capacities, and contract addresses.

- `setTotalAlchemicas`: Sets the total alchemica available across all parcels.

- `getAvailableAlchemica`: Returns the available alchemica in a parcel.

- `calculateTransferAmounts`: Calculates the amounts to be transferred based on a spillover rate.

- `lastClaimedAlchemica`: Returns the last time alchemica was claimed for a parcel.

- `claimAvailableAlchemica`: Allows the owner of a parcel to claim available alchemica.

- `getHarvestRates`: Returns the harvest rates for alchemica in a parcel.

- `getCapacities`: Returns the capacities for alchemica in a parcel.

- `getTotalClaimed`: Returns the total alchemica claimed for a parcel.

- `channelAlchemica`: Allows a parcel owner to channel alchemica to a parent ERC721 token and the great portal.

 - `getLastChanneled`: Returns the last timestamp of a channeling for a gotchi.

- `getParcelLastChanneled`: Returns the last timestamp of an altar channeling for a parcel.
batchTransferAlchemica: Batch transfers alchemica to multiple addresses.

- `batchTransferTokensToGotchis`: Batch transfers tokens to multiple gotchis.

- `setChannelingLimits`: Sets the channeling limits for different altar levels.
 
- `floorSqrt`: Calculates the floor square root of a number, likely used for calculations involving alchemica distribution.

- `_batchTransferTokens`: Internal function to batch transfer tokens, handling ERC20 transfers.
batchTransferTokens: Public function to batch transfer tokens, likely used for distributing alchemica or other tokens.

## Conclusion

The Aavegotchi Alchemica facet is a crucial part of the Aavegotchi ecosystem, responsible for managing Alchemica tokens. It allows users to interact with the Alchemica ecosystem by 
channeling, claiming, transferring, and managing Alchemica tokens. Overall, this facet is essential for the functionality and usability of the Aavegotchi ecosystem.