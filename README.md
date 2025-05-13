<p align="center">
  <a href="https://peifeng.li"><img width="184px" alt="logo" src="https://raw.githubusercontent.com/li-peifeng/li-peifeng.github.io/refs/heads/main/logo.png" />
  </a>
</p>

# Jellyfin Actor Refresh Script

This bash script addresses actor refresh issues encountered in Jellyfin and helps resolve an issue with Infuse not displaying actors correctly. It automates the process of refreshing actor metadata in Jellyfin, resolving inconsistencies and ensuring actors are displayed correctly in both Jellyfin and Infuse. 

**Note:** This script is a workaround and may not be the most optimized approach. It is generally intended to be run once or scheduled as a cron job. For information on setting up cron jobs, see [this link](https://www.ostechnix.com/a-beginners-guide-to-cron-jobs/). 


## Background

This script is inspired by and based on a PowerShell script created by [deltonio2](https://github.com/deltonio2) to address the following issues:

- **Jellyfin Actor Refresh Issue:** Jellyfin sometimes fails to refresh actor information properly. This issue is discussed in the Jellyfin thread: [jellyfin/jellyfin#8103](https://github.com/jellyfin/jellyfin/issues/8103)

While working with the script, it was discovered that this method also helps resolve a separate issue with Infuse:

- **Infuse Actor Display Issue:** Infuse may not display actors correctly if actor details are present in `.nfo` files. This script helps mitigate this issue by refreshing the actor metadata in Jellyfin, which in turn can improve actor display in Infuse.

This bash script provides a solution for Linux users who may not have PowerShell installed on their systems.

## Features

- **Refreshes actor metadata:** Automates API calls to Jellyfin to update actor information.
- **Helps resolve Infuse display issue:** Mitigates the issue of Infuse not showing actors correctly when details are in `.nfo` files.
- **Force flag:** Allows processing of all actors, regardless of their image tag status, using the `--force` flag.
- **Server ping check:** Verifies if the Jellyfin server is reachable.
- **Error handling:** Includes error handling for API calls and server availability.
- **Progress bar:** Displays a progress bar to visually track the refresh process.
- **Informative output:** Provides clear and colorful output with status messages and error reporting.
- **Continuous error check:** Stops the script if multiple consecutive errors occur.

## Usage

1. **Configuration:**
   - **Find your User ID:**
     - Access your Jellyfin server's web interface.
     - Navigate to the "Users" section in the administration panel.
     - Select the desired user.
     - The URL in your browser will contain the `userId`, for example: `http://jellyfin-server:8096/web/#/dashboard/users/profile?userId=XXXXXXXX` 
   - **Create or get an API Key:**
     - Go to your Jellyfin settings.
     - Navigate to "Advanced" and then "API Keys".
     - Click the button to generate a new API key.
     - Copy the displayed API key.

   - **Update the script:**
     - Replace `api_key` with your actual Jellyfin API key.
     - Replace `user_id` with your Jellyfin user ID.

2. **Running the script:**
   - Make the script executable: `chmod +x jellyfin_actor_refresh.sh`
   - To refresh actors without image tags: `./jellyfin_actor_refresh.sh`
   - To refresh all actors: `./jellyfin_actor_refresh.sh --force`

   **Note:** This script is written for bash. If you are using a different shell, please consult your shell's documentation for the appropriate way to execute scripts.

## Prerequisites

- `curl`
- `jq`
- `ping`
- `sed`
- `tail`
- `wc`

(These are usually installed by default on most Linux distributions. If not, use your package manager to install them.)

## Acknowledgements

- This script is heavily inspired by the PowerShell script created by [deltonio2](https://github.com/deltonio2).
- Thanks to the Jellyfin community for identifying and discussing the actor refresh issue.

## License

This script is released under the **GPL V3 License**.
