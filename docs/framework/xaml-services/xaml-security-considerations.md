---
title: "Důležité informace o zabezpečení pro jazyk XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b58719f36cd911497c5cd892610330688221e7ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-security-considerations"></a>Důležité informace o zabezpečení pro jazyk XAML
Toto téma popisuje osvědčené postupy pro zabezpečení v aplikacích, když používáte XAML a rozhraní .NET Framework XAML Services API.  
  
## <a name="untrusted-xaml-in-applications"></a>Nedůvěryhodné XAML v aplikacích  
 V nejobecnější smysl je nedůvěryhodný XAML libovolný zdroj XAML, který aplikace není specificky zahrnout nebo emitování.  
  
 XAML, který se zkompiluje do nebo uložené jako `resx`-typu prostředku v rámci důvěryhodné a podepsané sestavení není ze své podstaty nedůvěryhodné. XAML můžete důvěřovat tolik, kolik důvěřujete sestavení jako celek. Ve většině případů se pouze důvěryhodnosti aspektů přijít XAML, který je zdrojem XAML, který načítat z datového proudu nebo jiných vstupně-výstupní operace. Uvolněná XAML není konkrétní součást nebo funkce model aplikací s infrastruktury balení a nasazení. Sestavení však může implementovat chování, které zahrnuje načítání přijít XAML.  
  
 Pro nedůvěryhodné XAML, můžete by měly zpracovávat je obecně stejná jako by šlo nedůvěryhodnými. Použít sandboxing nebo jiných metaphors pravděpodobně nedůvěryhodné XAML zabránit v přístupu k důvěryhodný kód.  
  
 Povaha XAML možnosti dává XAML práva k vytváření objektů a nastavte jejich vlastnosti. Tyto schopnosti zahrnují také přístup k převaděče typů, mapování a přístup k sestavení v doméně aplikace pomocí rozšíření značek `x:Code` bloky a tak dále.  
  
 Kromě možnosti úroveň jazyka XAML slouží pro definici uživatelského rozhraní v mnoha technologií. Načítání nedůvěryhodné XAML může znamenat načítání škodlivý falšováním uživatelského rozhraní.  
  
## <a name="sharing-context-between-readers-and-writers"></a>Sdílení kontextu mezi čtení a zápis  
 Architektura rozhraní .NET Framework XAML Services XAML čtení a zápis XAML často vyžaduje sdílení čtečku XAML zapisovač XAML nebo sdílené kontext schématu XAML. Pokud píšete logiky smyčky uzlu XAML nebo poskytování vlastní Uložit cestu může být potřeba sdílení objekty nebo kontextů. Nesmí sdílet instance čtečky XAML, kontext schématu XAML nevýchozí nebo nastavení pro třídy čtečky nebo zapisovač XAML mezi důvěryhodné a nedůvěryhodné kódu.  
  
 Většina scénářů a operací zahrnujících XAML objekt zápis pro zálohování typu CLR na základě jednoduše použít výchozí kontext schématu XAML. Výchozí kontext schématu XAML explicitně neobsahuje nastavení, které by mohly ohrozit úplný vztah důvěryhodnosti. Proto je bezpečně sdílet kontextu mezi důvěryhodné a nedůvěryhodné součásti XAML čtečky nebo zapisovač. Pokud to uděláte, je však stále osvědčeným postupem takové čtení a zápis mějte samostatné <xref:System.AppDomain> oborů s jedním z nich speciálně určený nebo v izolovaném prostoru částečného vztahu důvěryhodnosti.  
  
## <a name="xaml-namespaces-and-assembly-trust"></a>Obory názvů jazyka XAML a vztah důvěryhodnosti sestavení  
 Základní nekvalifikované syntaxe a definice Interpretace jazyka XAML: vlastní mapování oboru názvů jazyka XAML k sestavení nerozlišuje mezi důvěryhodné a nedůvěryhodné sestavení jako načteno do domény aplikace. Z toho důvodu je technicky možné nedůvěryhodné sestavení zfalšovat mapování oboru názvů jazyka XAML určený důvěryhodné sestavení a zachycení deklarované objekt zdroji XAML a informace o vlastnosti. Pokud máte požadavky na zabezpečení k této situaci vyhnout, třeba vaše určený mapování oboru názvů jazyka XAML provést pomocí jedné z následujících postupů:  
  
-   Použijte plně kvalifikovaný název sestavení se silným názvem v žádné mapování oboru názvů jazyka XAML provedené XAML vaší aplikace.  
  
-   Omezit sestavení mapování na pevnou sadu referenční sestavení, vytvořením konkrétní <xref:System.Xaml.XamlSchemaContext> pro váš jazyk XAML čtečky a XAML objekt zapisovače. V tématu <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.  
  
## <a name="xaml-type-mapping-and-type-system-access"></a>Mapování typu XAML a typ systému přístup  
 XAML podporuje svůj vlastní systém typ, který v mnoha směrech je rovnocenný na tom, jak CLR implementuje systému základní typ CLR. Pro některé aspekty typ sledování, kde jsou při důvěryhodnosti rozhodování o typu, na základě jeho typu informací, však musí odložit na informace o typu CLR zálohování typy. Je to proto, že některé specifické možnosti vytváření sestav systému typ XAML jsou ponechány otevřené jako virtuální metody a nejsou proto plně pod kontrolou původní implementace rozhraní .NET Framework XAML Services. Tyto body rozšiřitelnosti existovat, protože systém typů XAML je rozšiřitelný, tak, aby odpovídaly rozšiřitelnosti jazyka XAML sám a možné alternativní strategie mapování typu versus výchozí implementace zálohovaná CLR a výchozí kontext schématu XAML. Další informace najdete v tématu konkrétní poznámky na několik vlastností <xref:System.Xaml.XamlType> a <xref:System.Xaml.XamlMember>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xaml.Permissions.XamlAccessLevel>
