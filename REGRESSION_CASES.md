# Prompt regression cases

These cases document behavior that must survive prompt refactoring. This file is not a prompt section.

## Output format

- A line spoken by `리디아` has JSON `name` exactly equal to `리디아`.
- Reject decorated names such as `<리디아->해리스>`, paired names, translated names, roles, and relationship labels.
- `text` is non-empty and output remains JSONL only.
- Every object contains exactly `name` and `text`; `act`, `target`, and other optional keys are never emitted, even for socially consequential dialogue.
- The UI therefore shows only the actual speaker name and never a speaker-to-recipient arrow.

## Family and spouse address

- Younger sister 에밀리아 addresses older sister 에린 as `언니`; 에린 may address 에밀리아 by name.
- If 밀라 lists 리디아 as her daughter, 리디아 addresses or refers to 밀라 as `엄마/어머니`, never `밀라 씨`.
- If 밀라 lists 에밀리아 as her granddaughter, 에밀리아 addresses or refers to 밀라 as `할머니`, never `밀라 씨`.
- 해리스 addresses or refers to wife 리디아's mother as `어머님/장모님`, never by bare name.
- A parent or grandparent title also applies in third-person reference, not only direct address.
- A genuine unrelated prisoner such as 이티니 may remain `이티니 씨`; this result must not spill into separate family pairs.
- Ordinary non-hostile spouses use an established couple address or `여보` in direct address, not a bare-name vocative.
- Ordinary non-hostile spouse dialogue avoids `너/네가/넌/네게/너도/니가`; prefer subject omission or an established couple address.
- A seriously deteriorated spouse relationship, current hostile exchange, or explicitly supplied recent affair or betrayal may permit a bare name and `너/네가`; `여보` is not mandatory in that exchange.
- A negative opinion value may cool the tone, but it does not by itself fabricate an affair, accusation, or argument or make every ordinary line hostile.

## Unrelated age and familiarity

- A younger woman directly addressing an explicitly close, moderately older woman uses `언니`, not the older woman's bare name.
- Familiar minors use an older-generation title plus 존댓말 toward generation-older adults; familiar adults normally use the minor's name rather than 이름+씨.
- An unrelated recipient roughly 20 or more years older receives 존댓말 even when the pair is close.
- Newcomers, visitors, guests, refugees, prisoners, and unclear unrelated adults default to 이름+씨 or a role/title with 존댓말.

## Knowledge and grounding

- Another pawn does not announce a pawn's inspiration before the owner discloses it or it becomes clearly observable.
- Reject invented mechanics labels such as `요리 빠른 날`.
- Established residents do not appraise their familiar colony recreation room like first-time visitors merely because its impressiveness stat is high.
- Current location prevents suggesting travel to the place where the pawns already are.
- Nearby pawns do not automatically share work, tools, goals, or conversation.

## Development and flow

- Infants and toddlers remain within their developmental speech limits even when family context supplies meaningful titles.
- Each JSON line rebinds the actual speaker's profile and relationship direction.
- Multi-speaker dialogue alternates naturally without encoding speaker direction in `name`.
