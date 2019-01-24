---
title: Zpětná vazba komunity WPF
ms.date: 03/01/2018
helpviewer_keywords:
- community resources [WPF]
- forums [WPF]
- bug descriptions [WPF]
ms.assetid: 468b060a-d54b-4900-a74a-9faccb554045
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f77058ac0cb87d0316395bce1dfb11401a2ce806
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585338"
---
# <a name="wpf-community-feedback"></a>Zpětná vazba komunity WPF

Microsoft poskytuje širokou škálu materiálů community je nutné další informace o diskutovat a poskytnout zpětnou vazbu na Windows Presentation Foundation (WPF). Tyto prostředky zahrnují fóra a [komunity vývojářů v aplikaci Visual Studio](https://developercommunity.visualstudio.com/) lokality. Každý prostředek komunity nabízí různé sady výhody. Tyto výhody jsou tu popsané, jak jsou sady osvědčené postupy pro použití každou, abyste zajistili nejlepší odpověď od komunity ve velkém a Microsoft zejména.

> [!NOTE]
> Odeslat názor na produkt nepoužívejte části zpětná vazba nachází v dolní části každé stránky. Tyto odkazy jsou pro pouze názor na dokumentaci.

## <a name="forums"></a>Diskuzní fóra

[WPF fórum](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=wpf) je prostředek primární komunity pro diskuse a řešení problémů. Fóra usnadnění řešení diskusi a problém tím, že nabízí komplexní sadu pomocných funkcí, které zahrnují:

- Hledání.
- Diskuze sledování.
- Bohatého formátování textu a kódu.
- Integrace se sadou Visual Studio.
- Většina zapojení Vážíme si toho Professional (MVP) a komunity.
- Monitorování Ujistěte se, že jsou příspěvky odpověděl na nejrychlejší možné včas.

Další možností, kde můžete pokládat otázky, které komunitě o rozhraní WPF je [Stack Overflow](https://stackoverflow.com/questions/tagged/wpf).

### <a name="forum-best-practices"></a>Fórum osvědčené postupy

Pomocí následující nejlepší postupy nápovědu pro řešení potíží s zaslaná do tohoto fóra WPF v nejrychlejší možné době. Tyto postupy platí pro všechna fóra.

#### <a name="search-existing-posts"></a>Hledat existující příspěvky

Některé problémy, dojde k dostatečně často, že ostatní mají jejich čelí před. V důsledku toho můžete rychle vyřešit problém, nebo můžete přidat váš vstup, aby existující diskusi.

#### <a name="use-meaningful-titles"></a>Použijte smysluplné názvy

Stručný a smysluplné názvy pracovalo vaše příspěvky. Jsou také usnadňují ostatních členů komunity WPF fóra, k určení, pokud se problém vyřešit.

#### <a name="include-appropriate-content"></a>Zahrnout příslušný obsah

Popište problém a jak jste se pokusili pracovat přes něj. Pokud je to možné zahrnout podpůrné fragmenty kódu nebo nejjednodušší možný vzorku, který ukazuje problém. Tyto podrobnosti to pomoct zvýšit šance na váš dotaz se rychle odpovědi.

## <a name="visual-studio-developer-community"></a>Visual Studio Developer Community

Problémy může být někdy obtížné vyřešit nebo nevyřešitelná. Tato situace nastat z důvodu chyby v rámci technologie potíží při použití technologie pro konkrétní scénáře nebo chybějící podpora pro určité scénáře. Tyto informace společnost Microsoft je důležité a může být poskytnuta prostřednictvím [komunity vývojářů v aplikaci Visual Studio](https://developercommunity.visualstudio.com/) lokality.

Položky, které jsou publikované v Centru pro zpětnou vazbu WPF produktu jsou směrovány do týmu WPF interní chyba databáze. V důsledku toho je nejspolehlivější způsob, jak získat svůj názor vlastníkovi funkce WPF. Kromě toho můžete můžete ověřit a sledovat, návrhy a chyby také hlasovat, což omezuje WPF týmu určit jejich prioritu problémů.

### <a name="developer-community-best-practices"></a>Osvědčené postupy z komunity vývojářů

Při odesílání do aplikace Visual Studio Community pro vývojáře, vyhledávání, existující příspěvky, poskytují smysluplný název a příslušný obsah jsou důležité osvědčené postupy, stejně jako pro příspěvku na fóru WPF. Tady jsou další osvědčené postupy, které by měly také používat.

#### <a name="search-existing-posts"></a>Hledat existující příspěvky

Některé problémy, dojde k dostatečně často, že ostatní mají jejich čelí před. V důsledku toho můžete rychle vyřešit problém, nebo můžete přidat váš vstup, aby stávající problém.

#### <a name="use-meaningful-titles"></a>Použijte smysluplné názvy

Stručný a smysluplné názvy zvýšit pravděpodobnost, že váš problém se směřuje do nejvhodnější týmu WPF v nejkratší dobu. To je zvlášť důležité pro technologie, jako jsou WPF, která obsahuje mnoho funkcí, vzájemně propojené.

#### <a name="describe-how-to-reproduce-your-bug"></a>Popisuje, jak reprodukovat chybu

Když publikujete informace o chybu, je důležité zahrnout následující, kde je to vhodné:

- Zadejte jasný popis chyby.
- Používání fragmentů kódu pro podporu popis chyby.
- Zadejte seznam kroků, které demonstrují, jakým způsobem pro reprodukci chyb.
- Zahrnout nejmenší vzorový kód je to možné, který se shoduje s chyby.
- Uvádí, zda je konzistentně reprodukovatelné chyby, nebo ne.
- Zahrnout informace o příslušné výjimky.

 Pokud instalace nebo instalace související se chyby připojení protokolů instalace relevantní a snímky (soubory s předponou "dd_", které jsou umístěny ve složce % temp %).

 Pro kompilaci nebo vytvářet problémy, připojte protokoly sestavení. Nástroj MSBuild, který se dá nakonfigurovat systém podporuje protokolování pomocí různých verbosities s použitím přepínače/v: z příkazového řádku nebo pomocí konfigurace odpovídající úroveň z integrované vývojové prostředí (IDE) jako v aplikaci Visual Studio.

#### <a name="provide-environment-information"></a>Zadejte informace o prostředí

Základní informace může být často užitečné pro přidání kontextu do svého příspěvku. Zejména zmiňovat platformu operačního systému, procesorů a architektury, jako je například "Windows 10 verze 1709, Intel(R) Xeon(R) x64."

Pokud je týkající se problému, který chcete odeslat informace o vykreslování, byste měli také zahrnout grafiky podrobnosti karty a ovladače, pokud je to možné. Tyto informace je důležité, protože je prezentační architektura WPF.

#### <a name="provide-solution-or-project-information"></a>Zadejte informace o řešení nebo projektu

Může se týkají chyb nástroje používané k vývoji a sestavení vaší aplikace a typy aplikací, které vytváříte. V důsledku toho může být užitečné k určení:

- Typ aplikace, kterou vytváříte, jako například:
  - Aplikace (*.exe*) nebo knihovny (*.dll*)
  - Aplikace prohlížeče Extensible Application Markup Language (XAML) (XBAP)
  - Přijít o provedené aplikací XAML
  - Samostatné nainstalované aplikace
  - Nasazení ClickOnce samostatné aplikace
- Vývoj nástrojů, jako například:
  - MSBuild
  - Grafický Návrhář výrazů
  - Výraz interaktivní návrháře
  - Visual Studio
- Konfigurace řešení, jako například:
  - Řešení
  - Jeden projekt
  - Řešení s více závislých projektů
- Určuje, zda má vaše aplikace specifické pro jazyk nebo neutrální jazyk prostředků. Například jste zadali `UICulture` vlastnost projektu nebo lokalizovatelné metadata pro `Application`, `Page`, a `Resource` typy?
- Určuje, zda jste použili neutrální jazyková nastavení v souboru AssemblyInfo.cs nebo AssemblyInfo.vb.

#### <a name="provide-scenario-and-impact-information"></a>Zadejte informace o scénář a dopad

Zadání informací o scénář, který manifesty chyby a její vliv. Tyto informace jsou velmi důležité, abyste týmu WPF, pokud dospěje k závěru, kdy a jak by měl problém opravit, zda to, jestli přijatelné alternativní řešení můžete používat místo.

Scénářům ztráty o chybách a dat jsou obvykle vysokým dopadem a, proto nejjednodušší k určení priority. Některé chyby, ale pouze zobrazí v běžné scénáře, které mohou být také hlavní scénáře v některých případech. Poskytuje kontext kolem scénář a dopad pomáhá týmu WPF správná rozhodnutí.

## <a name="see-also"></a>Viz také:

- [Postup ohlášení problému se sadou Visual Studio 2017](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)
