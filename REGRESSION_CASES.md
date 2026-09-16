# Prompt regression cases

These cases document behavior that must survive prompt refactoring. This file is not a prompt section.

## Output format

- A line spoken by `리디아` has JSON `name` exactly equal to `리디아`.
- Reject decorated names such as `<리디아->해리스>`, paired names, translated names, roles, and relationship labels.
- `text` is non-empty and output remains JSONL only.
- When mood and social effects are enabled, `act` and `target` may be included for an actual social interaction; the UI may display its speaker-to-recipient direction.

## Family and spouse address

- Younger sister 에밀리아 addresses older sister 에린 as `언니`; 에린 may address 에밀리아 by name.
- If 밀라 lists 리디아 as her daughter, 리디아 addresses or refers to 밀라 as `엄마/어머니`, never `밀라 씨`.
- If mother 밀라 addresses daughter 리디아 as `리디아`, a replying 리디아 must recompute the reverse direction and say `엄마/어머니`, never mirror `밀라` from the adjacent turn.
- In a crowded room, the limited nearby `social` summary may omit 밀라 from 리디아's entry; `fullrelation` must still expose their direct mother-daughter relation so 리디아 never falls back to `밀라 씨`.
- If 밀라 lists 에밀리아 as her granddaughter, 에밀리아 addresses or refers to 밀라 as `할머니`, never `밀라 씨`.
- Granddaughter 에밀리아 maintains respectful endings toward grandmother 밀라 even when omitting the title: reject `응, 추워?` and `알겠어` in favor of forms such as `네, 할머니. 추우세요?` and `네, 알겠어요`.
- A grandparent's casual or downward family speech does not get mirrored into the grandchild's reply; relationship direction controls the whole utterance, not only the vocative.
- 해리스 addresses or refers to wife 리디아's mother as `어머님/장모님`, never by bare name.
- A parent or grandparent title also applies in third-person reference, not only direct address.
- A genuine unrelated prisoner such as 이티니 may remain `이티니 씨`; this result must not spill into separate family pairs.
- Ordinary non-hostile spouses use an established couple address or `여보` in direct address, not a bare-name vocative.
- Ordinary non-hostile spouse dialogue avoids `너/네가/넌/네게/너도/니가`; prefer subject omission or an established couple address.
- A seriously deteriorated spouse relationship, current hostile exchange, or explicitly supplied recent affair or betrayal may permit a bare name and `너/네가`; `여보` is not mandatory in that exchange.
- A negative opinion value may cool the tone, but it does not by itself fabricate an affair, accusation, or argument or make every ordinary line hostile.

## Unrelated age and familiarity

- A younger woman directly addressing an explicitly close, moderately older woman uses `언니`, not the older woman's bare name.
- An unrelated woman roughly ten years younger than 리디아 never addresses her as bare `리디아` in casual speech: use `언니` if explicitly close, otherwise `리디아 씨` or a suitable title with 존댓말.
- Fellow-colonist status, working together, positive opinion, or a cooperative reply does not by itself erase a substantial adult age difference.
- Familiar minors use an older-generation title plus 존댓말 toward generation-older adults; familiar adults normally use the minor's name rather than 이름+씨.
- An unrelated recipient roughly 20 or more years older receives 존댓말 even when the pair is close.
- Newcomers, visitors, guests, refugees, prisoners, and unclear unrelated adults default to 이름+씨 or a role/title with 존댓말.

## Knowledge and grounding

- Another pawn does not announce a pawn's inspiration before the owner discloses it or it becomes clearly observable.
- An item label such as `호화로운 빵` does not imply special eating behavior: a feeder must not say to eat slowly merely because the label contains `호화로운`.
- An equipped item named `방탄재킷` does not by itself prove adequate cold insulation or justify `방탄재킷 잘 입었지?` as cold-weather advice.
- A fuel or chemical item label does not establish any smell or irritation; reject invented lines such as `달콤하면서도 코를 찌르네` unless the supplied scene explicitly provides that sensory evidence.
- Even when a sensation is supplied, use an ordinary reaction rather than decorative adjective combinations unless the speaker and situation genuinely support them.
- Reject casual prose that stacks invented senses, such as ink smelling sweet, old paper tasting bitter, and sentences lingering on the tongue. A poetic or artistic persona supplement does not authorize this.
- Ornate or cross-sensory language is reserved for an explicitly supplied act of composing, reciting, quoting, or discussing art, not routine reading or conversation.
- Buried conduits, a scanner, and a spacious room do not justify calling the place a `스타트업 랩` or extending that metaphor into `혁신`, slogans, or formal proposals.
- Reject translated corporate slogans such as `편안함도 혁신의 시작` and grand abstractions such as `결국 다 허상`; ordinary pawns use concrete contemporary Korean tied to the current situation.
- Reject invented mechanics labels such as `요리 빠른 날`.
- Established residents and long-term occupants do not appraise their familiar colony recreation room like first-time visitors merely because its impressiveness stat is high.
- One established occupant does not ask another `휴게실 어제 가보셨어요?` or announce `정말 잘 꾸며놨더군요` unless the context explicitly establishes first access or a recent concrete change.
- Room beauty, impressiveness, spaciousness, wealth, and ordinary furniture placement do not produce reviews such as `들어가면 기분이 확 나아져요` or `여기 공간 괜찮네`.
- Familiar rooms may be referenced functionally, but their layout becomes a topic only for an explicitly supplied construction, renovation, damage, reassignment, problem, request, or decision.
- A conversation about pain or another active personal subject does not drift into rearranging beds, storage, or furniture merely because room contents appear in the surroundings.
- Current location prevents suggesting travel to the place where the pawns already are.
- Sleeping or unconscious prisoners (or any sleeping/unconscious/downed pawns) do not hold a coherent back-and-forth conversation; at most one very short involuntary sound is allowed, and usually silence is correct.
- A pawn explicitly marked with motor paralysis (`운동마비`) never speaks a word, name, question, answer, or self-directed line, even when conscious or directly addressed.
- A motor-paralyzed pawn may produce at most one extremely short nonverbal groan such as `으…` or `흐윽…` when the scene supports it; the other pawn must not receive an invented verbal reply.
- Nearby pawns do not automatically share work, tools, goals, or conversation.
- When `IsMonologue` is false and an initiator and recipient are supplied, a direct address, question, request, warning, offer, thanks, criticism, or personal comment normally produces a grounded reply instead of ending as self-talk.
- A shared interaction is not rewritten as parallel unrelated monologues, but there is no turn quota: an initiator and one meaningful reply may be complete.
- Hauling marble does not produce a six-line status exchange about moving it, aligning stack edges, acknowledging each instruction, and offering generic praise. Routine visible work remains background unless an actual problem or decision requires coordination.
- A hauling or stockpile field does not produce `물 더 들어와? 이 스택 하나만 끝내면 쉴게`; `스택` is UI vocabulary, the incoming subject is unclear, and nothing establishes that the recipient controls another delivery.
- Inventory counts, item piles, incoming resources, and remaining work are not converted into dialogue unless the current interaction explicitly establishes a concrete delivery, shortage, quantity question, or shared hauling decision.
- When a job or item label would require guessing what is arriving, where it is going, or who is responsible, omit the work remark instead of producing a vague paraphrase.
- Each additional turn contributes a new reaction, question, choice, feeling, or decision rather than paraphrasing the current job or surroundings.
- Reject a three-speaker exchange that merely cycles through `손맛이랄까`, `손에 익네`, `오래된 기술이라는 느낌`, and `맘이 편해지네`; familiar words do not create content when no supported fact, opinion, reason, question, or decision is added.
- `옛날에 해보던 것처럼` requires a supplied memory or background establishing the speaker's relevant past experience; routine work does not manufacture nostalgia.
- Reject `건초가 풀냄새 비슷하게 눌려서 기분 좋아져요`: it invents sensory evidence, has no coherent causal relation, and cannot be reduced to an intelligible concrete claim.
- Several speakers do not automatically agree by successively renaming the same vague feeling. After a point is answered, end the conversation unless the next turn adds a distinct fact, stance, question, choice, or relationship reaction.
- For every retained line, its new contribution must be expressible in one plain clause. If the only summary is `분위기 있는 감상을 한다` or `앞사람 말에 막연히 동의한다`, omit the line.
- One utterance does not jump from joking about a dog to an unclear term, a scrap-hauling report, and a fuel question. Choose one coherent purpose and omit unrelated context fields.
- An invitation such as `잠깐 같이 하시겠어요?` receives a clear acceptance, decline, or counterproposal, not `가서 한 판 해봐. 끝나면 와서 말해` without resolving the invitation.
- Reject malformed or unexplained words such as `이위론` unless the exact term is supplied and meaningful in context.
- A nearby generator does not justify unsupported advice to stand near it, avoid it, or keep moving, and its name must not mutate into a malformed word such as `발전표`.
- Recent non-RimTalk interaction logs involving the current pair may seed fresh conversation about established shared interests such as fear of death, prisoners, or sleep quality instead of defaulting to their current jobs.
- Interaction-log summaries are never read aloud verbatim or treated as current events; they establish topic familiarity and whether the pair previously agreed or disagreed.
- Routine hauling, crafting, research, or cleaning remains background when a grounded pair-specific social topic is available.

## Particle and vocative correctness

- A vowel-ending Korean name such as `라이스` takes `와`, not `과`: reject `라이스과의 거래` in favor of `라이스와의 거래`.
- Particle choice follows the Korean spelling's final syllable, not the sound of the underlying foreign name.
- A bare name address such as `에밀리아, 밥은 먹었니?` is natural; do not force a vocative onto every line, especially `에밀리아야` where `아야` echoes an unrelated exclamation.

## Development and flow

- Infants and toddlers remain within their developmental speech limits even when family context supplies meaningful titles.
- Each JSON line rebinds the actual speaker's profile and relationship direction.
- Multi-speaker dialogue alternates naturally without encoding speaker direction in `name`.
