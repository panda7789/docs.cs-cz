---
title: Důležité informace o zabezpečení pro jazyk XAML
ms.date: 03/30/2017
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
ms.openlocfilehash: 1864910b339c74e3033fb4d6d8baebffada1a4f8
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071687"
---
# <a name="xaml-security-considerations"></a>Důležité informace o zabezpečení XAML

Tento článek popisuje osvědčené postupy pro zabezpečení v aplikacích při použití rozhraní XAML a .NET XAML Services API.

## <a name="untrusted-xaml-in-applications"></a>Nedůvěryhodný XAML v aplikacích

V nejobecnějším smyslu je nedůvěryhodný XAML jakýkoli zdroj XAML, který vaše aplikace konkrétně neobsahovala nebo nevyzařovala.

XAML, který je kompilován `resx`do nebo uložen jako prostředek typu v rámci důvěryhodného a podepsaného sestavení, není ze své podstaty nedůvěryhodný. XAML můžete důvěřovat stejně jako sestavení jako celku. Ve většině případů se zabýváte pouze aspekty důvěryhodnosti volné XAML, což je zdroj XAML, který načtete z datového proudu nebo jiné vstupně-v.V. Volné XAML není konkrétní součást nebo funkce aplikačního modelu s infrastrukturou nasazení a balení. Sestavení však může implementovat chování, které zahrnuje načítání volné XAML.

Pro nedůvěryhodné XAML byste měli zacházet obecně stejně, jako kdyby to byl nedůvěryhodný kód. Použijte sandboxing nebo jiné metafory, abyste zabránili možnému nedůvěryhodnému xaml v přístupu k důvěryhodnému kódu.

Povaha xaml schopnosti dává XAML právo vytvářet objekty a nastavit jejich vlastnosti. Tyto funkce také zahrnují přístup k převaděčům typů, mapování a přístup `x:Code` k sestavením v doméně aplikace pomocí rozšíření značek, bloků a tak dále.

Kromě možností na úrovni jazyka se XAML používá pro definici uživatelského rozhraní v mnoha technologiích. Načítání nedůvěryhodného xaml může znamenat načtení škodlivého uživatelského uživatelského uživatelského zařízení spoofingu.

## <a name="sharing-context-between-readers-and-writers"></a>Sdílení kontextu mezi čtenáři a spisovateli

Architektura služby .NET XAML services pro čtečky XAML a autory XAML často vyžaduje sdílení čtečky XAML se zapisovatelem XAML nebo sdílený kontext schématu XAML. Sdílení objektů nebo kontextů může být vyžadováno, pokud píšete logiku smyčky uzlu XAML nebo poskytujete vlastní cestu pro uložení. Nesdílejte instance čtečky XAML, nevýchozí kontext schématu XAML ani nastavení tříd čtečky a zapisovače XAML mezi důvěryhodným a nedůvěryhodným kódem.

Většina scénářů a operací zahrnujících zápis objektu XAML pro zálohování typu clr můžete použít pouze výchozí kontext schématu XAML. Výchozí kontext schématu XAML explicitně neobsahuje nastavení, která by mohla ohrozit úplnou důvěryhodnost. Je tedy bezpečné sdílet kontext mezi důvěryhodnými a nedůvěryhodnými komponentami čtečky/zapisovače XAML. Pokud to však uděláte, je stále osvědčeným postupem <xref:System.AppDomain> uchovávat takové čtenáře a autory v samostatných oborech, přičemž jeden z nich je speciálně určen/sandboxed pro částečnou důvěryhodnost.

## <a name="xaml-namespaces-and-assembly-trust"></a>Obory názvů XAML a vztah důvěryhodnosti sestavení

Základní nekvalifikovaná syntaxe a definice způsobu, jakým XAML interpretuje vlastní mapování oboru názvů XAML na sestavení, nerozlišuje mezi důvěryhodným a nedůvěryhodným sestavením načteným do domény aplikace. Proto je technicky možné pro nedůvěryhodné sestavení zfalšovat důvěryhodné sestavení zamýšlené mapování oboru názvů XAML a zachytit informace o deklarovaném objektu a vlastnostech zdroje XAML. Pokud máte požadavky na zabezpečení, abyste se této situaci vyhnuli, mělo by být zamýšleno mapování oboru názvů XAML provedeno jedním z následujících postupů:

- Použijte plně kvalifikovaný název sestavení se silným názvem v libovolném mapování oboru názvů XAML provedeném xaml vaší aplikace.

- Omezte mapování sestavení na pevnou sadu referenčních sestavení vytvořením specificképro <xref:System.Xaml.XamlSchemaContext> čtečky XAML a zapisovače objektů XAML. Viz třída <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.

## <a name="xaml-type-mapping-and-type-system-access"></a>Mapování typu XAML a přístup k systému typů

XAML podporuje vlastní typový systém, který je v mnoha ohledech rovnocenným způsobem, jak CLR implementuje základní systém typu CLR. Pro některé aspekty povědomí o typu, kde provádíte rozhodnutí o důvěryhodnosti o typu na základě informací o typu, byste však měli odložit na informace o typu v typech zálohování CLR. Důvodem je, že některé specifické možnosti vykazování systému typu XAML jsou ponechány otevřené jako virtuální metody a proto nejsou plně pod kontrolou původníimplementace .NET XAML Services. Tyto body rozšiřitelnosti existují, protože systém typu XAML je rozšiřitelný tak, aby odpovídal rozšiřitelnosti samotného xaml a jeho možných alternativních strategií mapování typu oproti výchozí implementaci podporované CLR a výchozímu kontextu schématu XAML. Další informace naleznete v konkrétních poznámkách <xref:System.Xaml.XamlType> k <xref:System.Xaml.XamlMember>několika vlastnostem aplikace a .

## <a name="see-also"></a>Viz také

- <xref:System.Xaml.Permissions.XamlAccessLevel>
