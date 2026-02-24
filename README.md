# Call Blocker

Call Blocker is a free and open-source iOS application available on the App Store, designed to block calls from known nuisance call sources.

## Features

* **Country-based Blocking**: Select from a list of countries to automatically download openly available lists of phone numbers known for nuisance calls and commercial solicitation.
* **Customizable Lists**: Add your own numbers to block or remove specific numbers from the downloaded lists. You can easily save your own customisations.
* **Persistent Customizations**: You can update your blocklist by pulling the latest data from the GitHub repository, and the application will seamlessly preserve your personal additions and removals.
* **Manual Updates**: To avoid any unwanted network traffic, all list updates (refreshing the blocklist) are always manual actions explicitly triggered by the user. There are no automated background blocklist refreshes.
* **Manual iCloud Backups**: Users have the option to back up their application data to iCloud. Similar to blocklist updates, these backups are strictly manual to ensure full control over network usage.

## Privacy First

One of the key benefits of Call Blocker is an uncompromising approach to privacy:
* **Zero Data Collection**: No user data is ever collected or processed.
* **No Telemetry**: No data is ever transmitted from your device to the application developer or any third party working with the developer. All operations happen locally on your device.

## Blocklists

The application's default blocklists are organized by country and are located in the `blocklists/` directory.

### Directory Structure
Each country has its own subdirectory named using its ISO 3166-1 alpha-2 country code (e.g., `US`, `GB`, `FR`). Inside each country's directory, the blocklist is stored in a JSON file named `<country_code>_blocklist.json` (e.g., `blocklists/US/US_blocklist.json`).

### JSON Format
The JSON file contains a list of entries, representing either a single nuisance number or a range of numbers. Each entry uses the following structure:
* `id`: The unique identifier for the entry, which must follow the format `<country_code>-<integer>` (e.g., `"FR-1"`).
* `type`: The type of the entry, which can be either `"number"` or `"range"`.
* `number`: The phone number to block (used if `type` is `"number"`).
* `start_number`: The first number in the blocked range (used if `type` is `"range"`).
* `end_number`: The last number in the blocked range (used if `type` is `"range"`).
* `description`: A description of the entry.
* `source`: The source of the entry.

**Note:** All phone numbers string values (whether `number`, `start_number`, or `end_number`) must be specified in full international format, meaning they should start with a `+` followed by the country dialling code and the number itself (e.g., `+18005551234`).

### Wildcard Expansion
iOS does not currently support wildcard characters for call blocking. Therefore, the application automatically processes these list entries and generates an exhaustive list of individual numbers from the defined ranges to replicate a wildcard-like functionality.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
