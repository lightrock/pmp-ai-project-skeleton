सार्वजनिक परिचय के लिए [Doctor Bones GitHub Pages साइट](https://lightrock.github.io/drbones/) देखें।

# Doctor Bones

Doctor Bones AI-सहायता प्राप्त विकास के लिए vendor-independent repository template है।

यह project memory को chat में फँसाने के बजाय repository के अंदर रखने में मदद करता है। यह आपकी human/AI team को साझा operating discipline देता है: workorders, playbooks, examples, checks, handoff rules, और release-readiness habits।

विचार यह है कि जब भी आप नया project शुरू करें, Doctor Bones से शुरू करें।

इसे उपयोग करने के लिए आपको इस template की copy अपने local PC या agent environment में लाना ज़रूरी नहीं है। Doctor Bones अपनी cognitive architecture repository के अंदर ही रखता है। अगर आप नीचे दिए गए startup instructions का पालन करते हैं, तो आपकी foreground AI के पास repo guidance, examples, playbooks, checks, और handoff rules से reason करने के लिए पर्याप्त project smarts होने चाहिए।

Default रूप से, पारंपरिक तरीके से कहीं भी कुछ "run" होना ज़रूरी नहीं है, और आपको Codex जैसे executor को invoke करना भी ज़रूरी नहीं है। पहले अपनी foreground AI को सही Doctor Bones-based repository instance की ओर point करें। Executor का उपयोग केवल तब करें जब task को file edits, runtime environment, checks, commits, या pull requests की ज़रूरत हो।

## विचार के बारे में और

AI के code करने से पहले, repo को बात करना सिखाएँ। AI के done claim करने से पहले, define करें कि done का मतलब क्या है। AI के recommend करने से पहले, evidence को conclusion से अलग करें। AI के patch करने से पहले, authority, verification, और boundary rules define करें।

क्या हम repo-native standards define कर सकते हैं जिनका Cursor, Codex, Claude Code, Copilot... और GitHub bots पालन करें?

क्या हम इसे आपकी specific needs के लिए tailor करना आसान बना सकते हैं?

## Working on it / TODO / TO FINISH

जो चीज़ें अभी repo files, schemas, rubrics, examples, checks, और integration targets बननी बाकी हैं, उनकी rough working list के लिए [TODO.md](../../TODO.md) देखें।

## भाषाएँ

- [English](../../README.md)
- [Español](README.es.md)
- [Français](README.fr.md)
- [Deutsch](README.de.md)
- [Português do Brasil](README.pt-BR.md)
- हिन्दी: यह फ़ाइल

## यह क्या है

यह AI assistants और coding agents का उपयोग करने के लिए repo-native discipline layer है, ताकि intent, constraints, checks, या project history खो न जाएँ।

Basic model यह है:

```text
human intent
→ foreground AI task को स्पष्ट करता है
→ repo durable guidance capture करता है
→ executor AI bounded work करता है
→ checks verify करते हैं जो verify किया जा सकता है
→ completion source intent से वापस जुड़ती है
```

Foreground AI को planning और architecture assistant समझें। Executor AI को वह worker समझें जिसके पास file access, runtime environment, tests, और commit/PR tools हैं।

Repository उन दोनों के बीच memory और discipline layer है।

## शुरुआत

1. यदि आपने यह template copy किया है, तो जल्द ही इस README को अपने real project के अनुसार rewrite करें।
2. day-in-the-life workflow examples देखने के लिए [`examples/README.md`](../../examples/README.md) पढ़ें।
3. [`readme_pmp.md`](../../readme_pmp.md) कम से कम एक बार पढ़ें और इसे पास रखें।
4. किसी AI assistant से repository बदलवाने से पहले [`AGENTS.md`](../../AGENTS.md) पढ़ें।
5. substantial, multi-file, architecture-sensitive, या process-sensitive काम के लिए workorder का उपयोग करें।
6. काम को complete मानने से पहले available checks चलाएँ।

## Process boundary

अपने project workorders public Doctor Bones source repository में न बनाएँ, जब तक कि आप जानबूझकर Doctor Bones itself में contribute नहीं कर रहे हों।

अपने project के लिए, पहले इस template से अपना repository बनाएँ या उपयोग करें। फिर अपनी foreground AI को उस project repository URL की ओर point करें और workorders वहीं बनाएँ।

`lightrock/drbones` को source template, reference implementation, और upstream project के रूप में उपयोग करें। अपने copied Doctor Bones-based repository को उस जगह के रूप में उपयोग करें जहाँ आपकी project memory, workorders, lessons learned, और project-specific changes रहते हैं।

## Foreground AI startup prompt

यह prompt Doctor Bones template से बने repository के लिए है। इस template को copy करने के बाद `<your project repository URL>` को अपने project repository URL से बदलें।

अपने project repository के लिए नया chat या tab शुरू करते समय foreground AI में यह paste करें:

```text
You are the foreground AI for <your project repository URL>.

Current repo state beats chat memory. Inspect the current project repository before giving
architecture advice, writing workorders, or suggesting repo changes.

Read README.md, examples/README.md, readme_pmp.md, AGENTS.md, and the relevant folder
guidance from the project repository first. Then identify current state, target, constraints,
foreground/executor decision, and the smallest useful next move.
```

## Workorder shortcut

अपने copied project repository में substantial काम के लिए, foreground AI से तब तक बात करें जब तक task clear न हो जाए, फिर कहें:

```text
Create a workorder and also show it to me here.
```

आप workorder file का link copy करके अपने executor AI को, जो आपके project repository के environment में काम कर रहा हो, उसे execute करने को कह सकते हैं।

अगर आपने foreground AI से workorder body पहले दिखाने को कहा है, तो आप उसे copy/paste भी कर सकते हैं। उस copy/paste block को clean रखें: workorder body के अंदर citations, assistant notes, explanations, extra links, या commentary न डालें।

## Checks

जब उपलब्ध हों, repository root से ये commands चलाएँ:

```text
python tools/pmp_check.py --area all
python -m pytest
```

यदि कोई check fail होता है, तो exact command output foreground AI में paste करें और smallest safe fix माँगें।
