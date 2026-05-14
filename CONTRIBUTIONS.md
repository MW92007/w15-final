# CONTRIBUTIONS

> **Required for ALL tiers.** Replace the bracketed prompts with your own
> answers. Honesty is graded; volume is not. One paragraph per section is
> usually enough — be specific, not impressive.

---

## 1. Starting Point

My starting point was from a clone of the W15 template. I had fallen behind and it was more reasonable to start from somewhere.

> **Example:** *"I started from my own W14 repo and pulled MapManager.cs and
> ExplorationUI.cs from the W15 template. My existing GameContext, models,
> and migrations carried forward unchanged."*
>
> **Or:** *"I started from a fresh clone of the W15 template because my own
> code stopped working after W13 and I couldn't recover it."*

---

## 2. What I Added

AdminService.MostDangerousRoom() - LINQ that uses GroupBy on the rooms that monsters are present in and sums up their health. It then orders the table and then pulls the first (highest value) from the table and displays the room with the highest sum of HP currently no the map.

AdminService.InventoryAudit() - LINQ that uses GroupBy to pair all items in the player inventory into their ContainerType. Chest, Inventory, MonsterLoot. The method then prints each table with their respective items.

Slime.cs - New Slime type enemy. The Slime has a unique attribute called GelatinousBile which acts as a 'burst attack' with each attack dealing more damage than the last. The power and amount of attacks is equal to the value of GelatinousBile. A Slime called 'Luke the Meistor of Slime' is added into the 'SeedFinalWorld.sql' and thus loaded on game start. He is positioned in the Hidden Shrine and currently has the highest HP and damage potential.

> **Example:**
> - `AdminService.MostDangerousRoom()` — LINQ `GroupBy` on `Monster.CurrentRoomId`
>   summing Health to find the riskiest area. Wired into the admin menu.
> - New `Orc : Monster` subclass with a `Strength` stat. New migration
>   `AddOrcMonster`, plus one seed row added to `SeedFinalWorld.sql`.
> - Added a `Shop` container in Town Square that exchanges items for gold.
>   New `Shop : Container` subclass, `Player.Gold` field, two new migrations.

---

## 3. What I Used From the Template / AI / Other Sources

Almost all of my program is from the template. I did not give myself as much time as I should have. While  I programmed most of my additions, AI was used to bug fix and was used heavily in the construction of the InventoryAudit() method.

> **Example:**
> - `MapManager.cs`, `ExplorationUI.cs`: used as-is from the W15 template.
> - `GameEngine.HandleChest`: copied from the W15 template, then modified
>   to add a "magical inspect" option for cursed chests.
> - `AdminService.MonsterCensus`: my own code, but the `GroupBy` pattern is
>   based on the W12 in-class `ListItems` example.
> - GitHub Copilot helped me draft the regex in `Shop.ParseTradeCommand`.
>   I rewrote ~half of it after testing.

---

## 4. Reflection on This Project (one paragraph)

The most difficult part of my project was the EntityFramework regarding enemies. I went through many itterations when it came to what enemy to add just because
they would refuse to migrate properly. I believe I have a better handle on migration and I believe I could add more monster types reasonably going forward. The
biggest help was going into SQLManagamentServer and manually adding in my monster Luke the Meistor of Slime. I was making an attempt to shoot for the A-tier, but I don't know if I quite made it.

> **Example:** *"The hardest part was figuring out why my Shop migration
> kept breaking — I'd forgotten to add the discriminator value in
> GameContext, so EF Core kept generating an empty migration. Took me an
> hour with the migration script generator to spot it. If I had another
> week I'd add a quest log, because I think the data model would be a fun
> exercise (Quest entity + Player→Quest many-to-many + a goal-state checker)."*

---

## 5. Course Feedback (NOT graded — please be candid)

Help me make this class better next time. **This section is not part of
your project grade.** I read it after grades are submitted, and I'd much
rather hear "week X was painful because Y" than diplomatic non-answers.
Concrete > polite.

**What did you learn that genuinely stuck with you?**
Migrations and data tables were very interesting to work with and I'd like to look further into it.

**What did you like about the course?**
I like the class in general to be honest, I felt like it was paced well.

**What didn't work for you?**
[What was confusing, slow, repetitive, or disconnected from the rest of
the work? Be specific so I can actually fix it.]

**What surprised you?**
[Something you expected to be easy but wasn't, or vice versa. Or a moment
where a concept clicked unexpectedly.]

**What was the hardest part of the semester (not just this project)?**
[A particular week, concept, debugging session, or assignment. Why?]

**What would you ADD to next year's version?**
[A topic, a tool, more practice on something, a guest speaker, anything.]

**What would you REMOVE or shorten?**
[Anything that felt like filler, redundant, or off-topic from your
perspective. Honest answers help — I literally rewrite the rubric and
materials each year based on this section.]

**Anything else?**
[Open-ended. Wins, frustrations, advice you'd give future students,
requests, or just a sentence about your overall experience.]

---

## How this is graded

**Sections 1-4** are the **gate to all rubric tiers.** Without a complete
and honest accounting of your starting point, additions, sources, and
project reflection, the project caps at 50% regardless of code quality.

- **Base/B/A/A+** all require Sections 1-4 to be filled out and to match
  what's actually in your repo.
- During your final presentation I may ask you to walk through any file
  you describe yourself as "added" or "modified" — be ready.
- Using template code with clear attribution is fine and earns full credit.
  Claiming to have written code you didn't is not, and will be graded
  as such (zero on the affected tier).

**Section 5 is not graded.** It exists to make the class better. A blank
Section 5 won't lower your grade; an honest critical Section 5 won't
either. The only "wrong" answer there is a fake one.

Think of Sections 1-4 as the README every PR needs: a short story about
what changed and why. It's a real engineering skill, and it's the most
reliable way for me to grade what you actually did.
