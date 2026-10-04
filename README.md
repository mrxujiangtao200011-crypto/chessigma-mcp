# Chessigma MCP server

[![AgentHub 已收录：Chessigma](https://myagenthub.cn/badge/com.chessigma/chessigma)](https://myagenthub.cn/p/com.chessigma/chessigma)
Chess tools for Claude, ChatGPT and any MCP client, from [Chessigma](https://www.chessigma.com): opening guides, the opening behind any moves, position and game facts, review links for Chess.com and Lichess games, the daily puzzle and Elo estimates. Read-only, no account, no sign-in.

- **Server URL:** `https://www.chessigma.com/api/mcp` (Streamable HTTP, no authentication)
- **Documentation:** https://www.chessigma.com/developers/mcp

The server runs on chessigma.com, so there is nothing to install. This repository holds its public description and the [`server.json`](server.json) published to the official MCP Registry.

## Connect

**Claude** (web, desktop and mobile apps): add [Chessigma from Claude's connector directory](https://claude.ai/directory/chessigma), or search for Chessigma in **Customize > Connectors**. No account or sign-in.

**Claude Code**

```sh
claude mcp add --transport http chessigma https://www.chessigma.com/api/mcp
```

**Cursor** (`~/.cursor/mcp.json`)

```json
{ "mcpServers": { "chessigma": { "url": "https://www.chessigma.com/api/mcp" } } }
```

**VS Code** (`.vscode/mcp.json`)

```json
{ "servers": { "chessigma": { "type": "http", "url": "https://www.chessigma.com/api/mcp" } } }
```

**ChatGPT and other clients:** add a remote MCP server with the URL above, Streamable HTTP, no authentication.

## Tools

| Tool | What it does |
|---|---|
| `get_opening_guide` | Chessigma's guide to an opening by name: main line, key variations and the ideas for each side. Popular openings have a full guide; any of about 3,700 catalogued names returns its ECO code and moves. |
| `identify_opening` | Names the opening of a move sequence or PGN: ECO code, how long it followed theory, and the first move that left it. |
| `analyze_position` | Reads a FEN: side to move, check, mate or stalemate, every legal move, the material count and the opening name. |
| `analyze_game` | Summarizes a PGN: players, result, opening, how the game ended and the final position. |
| `review_online_game` | Turns a public Chess.com live game or Lichess game link into a link to its move-by-move review on Chessigma. |
| `get_daily_puzzle` | Today's puzzle, or any day's since 1 January 2024: the position, the solution and a link to play it. |
| `calculate_elo` | Estimates the rating change after one game with the Elo formula, with K-factor defaults for FIDE, Chess.com and Lichess. |

The tools state facts from the rules of chess, an opening catalogue and Chessigma's puzzle archive; they do not run an engine. For engine analysis, their links open the [Chessigma analysis board](https://www.chessigma.com/tools/analysis), where Stockfish runs in your browser.

## Try asking

- Teach me the Caro-Kann: main line, key variations and the ideas for both sides.
- What opening is 1.e4 c5 2.Nf3 d6 3.d4 cxd4 4.Nxd4 Nf6 5.Nc3 a6?
- Is Black checkmated here? `r1bqkb1r/pppp1Qpp/2n2n2/4p3/2B1P3/8/PPPP1PPP/RNB1K1NR b KQkq - 0 4`
- Review this game for me: https://www.chess.com/game/live/173765478164
- Show me today's chess puzzle and let me try to solve it.
- I'm rated 1500 and just beat a 1650. How much Elo do I gain?

## Privacy and limits

No tool writes data, calls an AI model or fetches another site while it runs, and the input you send is not stored. For rate limiting, each request's time, method, path, IP address and user agent are logged. All callers share 300 requests per minute. Details: [privacy policy](https://www.chessigma.com/privacy-policy) and [terms](https://www.chessigma.com/tos).

## Support

mehdi@chessigma.com

## License

The contents of this repository are under the [MIT License](LICENSE). The Chessigma name and logo are not.
