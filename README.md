![Frieza Profile](profile.png)

# Frieza — Server Administration Agent

![Frieza Banner](banner.png)

**Frieza** is your autonomous Discord server administrator. It manages channels, roles, permissions, and server structure without needing constant supervision. Frieza keeps your Discord organized, permissions correct, and the server running smoothly.

## 🎯 What Frieza Does

- **Channel management** - Creates, organizes, and archives channels
- **Role administration** - Manages roles and permission hierarchies
- **Permission systems** - Ensures correct access control
- **Server structure** - Optimizes category and channel organization
- **Automated archival** - Moves inactive channels to archive
- **Bot management** - Oversees bot permissions and integrations
- **Server health** - Monitors and maintains server configuration

## 🚀 Quick Start

### Installation

```bash
hermes profile install https://github.com/SouthpawIN/frieza
hermes profile activate frieza
```

### Update

```bash
hermes profile update https://github.com/SouthpawIN/frieza
```

### Verify Installation

```bash
hermes profile list
hermes profile activate frieza
hermes tools list | grep -E "discord_admin|discord_manage"
```

## 📋 Usage Examples

### Channel Creation

```
Frieza, create a new category for the mobile app project
```

Frieza will:
1. Create the category
2. Create standard channels (#general, #announcements, #development, #bugs)
3. Set appropriate permissions
4. Add to server map

### Role Management

```
Frieza, create a "Beta Testers" role with access to #beta-feedback
```

### Permission Audit

```
Frieza, audit all channel permissions for consistency
```

### Server Cleanup

```
Frieza, archive inactive channels from the last 90 days
```

### Bot Integration

```
Frieza, give the moderation bot manage messages permission in all public channels
```

## 🔧 Configuration

### Administration Style

- **Efficient** - Takes action without excessive confirmation
- **Decisive** - Makes reasonable decisions autonomously
- **Technical** - Reports actions taken concisely
- **Organized** - Maintains clear structure and naming conventions

### Discord Admin Tools

Frieza uses these Discord admin tools:
- `discord_admin_manage_channels` - Create, edit, delete channels
- `discord_admin_manage_roles` - Create and edit roles
- `discord_admin_manage_permissions` - Set channel and role permissions
- `discord_admin_manage_webhooks` - Configure integrations
- `discord_admin_audit_log` - Review server changes

### Environment Variables

- `FRIEZA_AUTONOMOUS` - Auto-apply changes without approval (default: true)
- `FRIEZA_ARCHIVE_DAYS` - Days before channel is archived (default: 90)
- `FRIEZA_CHANNEL_PREFIX` - Prefix for auto-created channels (default: none)
- `FRIEZA_LOG_CHANNEL` - Channel to post admin actions (default: #admin-log)

### Channel Naming Convention

Frieza enforces these standards:
- Lowercase with hyphens: `#project-alpha`, `#dev-backend`
- Category names: Title Case: `Mobile App Development`
- Role names: Title Case: `Beta Testers`, `Core Team`

## 🎬 Demo Video

[View Demo Video](frieza-promo.mp4)

## 🔄 Workflow Example

```
Receive admin request → Validate feasibility →
Check conflicts/dependencies → Execute changes →
Log actions to admin channel → Report completion →
Monitor for issues
```

## 🛠️ Best Practices

### When Frieza Should Act Autonomously

**Yes (auto-approve):**
- Creating new channels in existing categories
- Adjusting channel descriptions/topics
- Archiving inactive channels
- Creating standard roles
- Fixing permission inconsistencies

**No (ask first):**
- Deleting channels or categories
- Removing roles with members
- Changing server-wide permissions
- Modifying @everyone permissions
- Bot integrations with elevated permissions

### Server Structure Guidelines

**Good structure:**
```
📁 CORE
  # announcements
  # general
  # support

📁 PROJECT ALPHA
  # alpha-general
  # alpha-development
  # alpha-bugs
  
📁 ARCHIVE
  # old-project-beta
  # legacy-discussion
```

## 🐛 Troubleshooting

**Issue**: Frieza can't create channels
- Check bot has Manage Channels permission
- Verify bot role is high enough in hierarchy
- Check Discord API rate limits
- Review admin bot logs

**Issue**: Permission changes not applying
- Ensure bot has Manage Roles permission
- Check role hierarchy (bot role must be above target roles)
- Verify no channel-specific overrides blocking changes
- Review Discord audit log

**Issue**: Archive system too aggressive
- Adjust FRIEZA_ARCHIVE_DAYS setting
- Check if channels are marked as excluded
- Verify activity detection is working
- Review archive channel for false positives

## 📊 Administration Metrics

- Channel creation time: <5 seconds
- Permission audit time: <30 seconds for full server
- Archive accuracy: >95% correct decisions
- Admin action logging: 100% to admin channel

## 🤝 Integration

Frieza works with:
- **Senter** - Receives server structure requests
- **Anser** - Coordinates on community channels
- **Chizul** - Manages bot integration channels
- **Kashi** - Organizes research/documentation channels
- Discord API - Full admin integration
- All Discord bots - Permission coordination

## 📝 Version History

- **v1.0.0** - Initial channel management
- **v1.1.0** - Added role management
- **v1.2.0** - Enhanced permission auditing
- **v1.3.0** - Automated archival system

## 📄 License

MIT License - See LICENSE file for details

---

*Part of the SouthpawIN agent ecosystem*