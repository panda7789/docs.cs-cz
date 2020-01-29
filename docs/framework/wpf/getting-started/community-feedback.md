---
title: Komunitní materiály
ms.date: 03/01/2018
helpviewer_keywords:
- community resources [WPF]
- forums [WPF]
- bug descriptions [WPF]
ms.assetid: 468b060a-d54b-4900-a74a-9faccb554045
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9e903045195d6f464659876334f7fedc5c695e9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733805"
---
# <a name="wpf-community-feedback"></a>Názory komunity WPF

Microsoft zveřejňuje celou řadu prostředků komunity, abyste se dozvěděli, projednali a poskytli zpětnou vazbu k Windows Presentation Foundation (WPF). Tyto prostředky zahrnují fóra a web [komunity vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/) . Každý komunitní prostředek nabízí jinou sadu výhod. Tyto výhody jsou popsány zde, jako je sada osvědčených postupů pro použití každého, aby bylo zajištěno, že nejlepší reakce z komunity na velké a společnosti Microsoft zejména.

> [!NOTE]
> Nepoužívejte část zpětné vazby nacházející se v dolní části každé stránky k odeslání zpětné vazby produktu. Tyto odkazy jsou k diskladně pouze pro názory na dokumentaci.

## <a name="forums"></a>Diskuzní fóra

[Fórum WPF](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=wpf) je primární komunitní prostředek pro diskuzi a řešení problémů. Fóra usnadňují řešení diskusí a problémů tím, že nabízí ucelenou sadu podpůrných funkcí, které zahrnují:

- Prohledávají.
- Sledování diskuzí.
- Formátování textu a kódu ve formátu RTF.
- Integrace sady Visual Studio.
- Nejlepší profesionální specialista (MVP) a komunitní zapojení.
- Monitorování, aby bylo zajištěno, že příspěvky budou v nejrychlejší možné době reagovat.

Další možností, jak můžete klást otázky komunitě týkající se WPF, je [Stack Overflow](https://stackoverflow.com/questions/tagged/wpf).

### <a name="forum-best-practices"></a>Osvědčené postupy pro fórum

Pomocí následujících osvědčených postupů můžete řešit problémy, které se publikují do fóra WPF v nejkratší možné době. Tyto postupy platí pro všechna fóra.

#### <a name="search-existing-posts"></a>Hledat existující příspěvky

K některým problémům dochází dostatečně daleko, než je někdo jiný. V důsledku toho můžete problém rychle vyřešit, nebo můžete přidat vstup do existující diskuze.

#### <a name="use-meaningful-titles"></a>Použití smysluplných názvů

Stručné a smysluplné názvy zlepšují zjistitelnost vašich příspěvků. Také usnadňují ostatním členům komunity WPF fóra, aby zjistili, jestli můžou problém vyřešit.

#### <a name="include-appropriate-content"></a>Zahrnout příslušný obsah

Popište problém a způsob, jakým jste se pokusili pracovat. Pokud je to možné, zahrňte podpůrné fragmenty kódu nebo nejjednodušší možnou ukázku, která demonstruje váš problém. Všechny tyto podrobnosti pomůžou zvýšit pravděpodobnost, že se Váš dotaz rychle odpoví.

## <a name="visual-studio-developer-community"></a>Komunita vývojářů sady Visual Studio

Problémy může někdy být obtížné vyřešit nebo nevyřešitelná. Tyto situace nastanou kvůli chybám v technologii, potížím s používáním technologie pro konkrétní scénáře nebo nedostatku podpory pro konkrétní scénáře. Tyto informace jsou důležité pro společnost Microsoft a mohou být poskytovány prostřednictvím webu [komunity vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/) .

Položky, které jsou publikovány v centru Feedback v produktu WPF, jsou směrovány do interní databáze interních chyb týmu WPF. V důsledku toho je nejspolehlivější způsob, jak získat zpětnou vazbu k vlastníkovi funkce WPF. Kromě toho můžete ověřovat a sledovat návrhy a chyby a také hlasovat, které pomáhají týmu WPF upřednostnit problémy.

### <a name="developer-community-best-practices"></a>Osvědčené postupy komunity vývojářů

Při odesílání do komunity vývojářů sady Visual Studio, hledání stávajících příspěvků, poskytování smysluplného titulu a vhodného obsahu, jsou důležité osvědčené postupy, stejně jako při publikování do fóra WPF. Níže jsou uvedené další osvědčené postupy, které byste měli použít.

#### <a name="search-existing-posts"></a>Hledat existující příspěvky

K některým problémům dochází dostatečně daleko, než je někdo jiný. V důsledku toho můžete rychle vyřešit váš problém, nebo můžete svůj vstup přidat k existujícímu problému.

#### <a name="use-meaningful-titles"></a>Použití smysluplných názvů

Stručné a smysluplné názvy zvyšují možnost, že váš problém je v nejkratší době přesměrován do nejvhodnějšího týmu WPF. To je důležité hlavně pro technologie, jako je WPF, která obsahuje mnoho vzájemně souvisejících funkcí.

#### <a name="describe-how-to-reproduce-your-bug"></a>Popište, jak reprodukování chyby.

Při odesílání informací o chybě je důležité zahrnout následující, pokud je to relevantní:

- Zadejte jasný popis chyby.
- Pro podporu popisu chyby použijte fragmenty kódu.
- Zadejte seznam kroků, které demonstrují, jak chybu znovu vytvořit.
- Zahrňte nejmenší možnou ukázku kódu, který reprodukuje chybu.
- Uvádí, zda je chyba konzistentně reprodukovatelná, nebo ne.
- Zahrňte relevantní informace o výjimce.

 Pokud je chyba instalace nebo instalace s nastavením, připojte příslušné instalační protokoly a snímky (soubory s předponou "dd_", které jsou umístěny ve složce% Temp%).

 V případě problémů kompilace nebo sestavení připojte protokoly sestavení. Systém MSBuild se dá nakonfigurovat tak, aby podporoval protokolování s různými podrobnostmi, a to pomocí přepínače/v: z příkazového řádku nebo konfigurací vhodné úrovně z integrovaného vývojového prostředí (IDE), jako je Visual Studio.

#### <a name="provide-environment-information"></a>Zadání informací o prostředí

Informace na pozadí jsou často užitečné pro přidání kontextu do příspěvku. Konkrétně uveďte platformu operačního systému, rodinu procesorů a architekturu, například Windows 10 verze 1709, Intel (R) Xeon (R), x64.

Pokud je problém, o který se chystáte, vztahují k vykreslování, měli byste také zahrnout grafickou kartu a podrobnosti o ovladačích, pokud je to možné. Tyto informace jsou důležité, protože WPF je prezentační architektura.

#### <a name="provide-solution-or-project-information"></a>Zadejte informace o řešení nebo projektu.

Chyby se mohou týkat nástrojů používaných pro vývoj a sestavování aplikací a typů aplikací, které vytváříte. V důsledku toho může být užitečné zadat:

- Typ aplikace, kterou vytváříte, například:
  - Aplikace ( *. exe*) nebo knihovna ( *. dll*)
  - Aplikace prohlížeče jazyk Extensible Application Markup Language (XAML) (XAML) (XBAP)
  - Volná aplikace XAML
  - Samostatné instalované aplikace
  - Samostatná aplikace nasazené v ClickOnce
- Vývojový nástroj, jako je například:
  - MSBuild
  - Návrhář grafiky výrazů
  - Interaktivní návrhář výrazů
  - Visual Studio
- Konfigurace řešení, jako například:
  - Řešení
  - Jeden projekt
  - Řešení s více závislými projekty
- Určuje, jestli má vaše aplikace prostředky pro konkrétní jazyk nebo jazykově neutrální prostředky. Například jste zadali vlastnost projektu `UICulture` nebo lokalizovatelné metadata pro `Application`, `Page`a `Resource` typy?
- Bez ohledu na to, zda jste v souboru AssemblyInfo.cs nebo AssemblyInfo. vb použili nastavení neutrálního jazyka.

#### <a name="provide-scenario-and-impact-information"></a>Zadejte informace o scénáři a dopadu

Poskytněte informace o scénáři, který manifestuje chybu a její dopad. Tyto informace jsou velmi důležité pro tým WPF, když se rozhodne, kdy, kdy a jak by měl být problém vyřešen, nebo jestli se místo toho dá použít přijatelné alternativní řešení.

Scénáře selhání a ztráty dat jsou obvykle vysokým dopadem a proto je nejjednodušší upřednostnit. Některé chyby se ale zobrazují jenom v neobvyklých scénářích, které můžou být v některých případech taky hlavní scénáře. Poskytnutí kontextu kolem scénáře a dopadu pomáhá týmu WPF dělat správné rozhodnutí.

## <a name="see-also"></a>Viz také:

- [Nahlášení problému se sadou Visual Studio](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)
