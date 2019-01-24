---
title: Důležité informace o zabezpečení pro jazyk XAML
ms.date: 03/30/2017
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
ms.openlocfilehash: 6cd09295f9dac26011652d6b0a33318841b04072
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648359"
---
# <a name="xaml-security-considerations"></a>Důležité informace o zabezpečení pro jazyk XAML
Toto téma popisuje doporučené postupy pro zabezpečení v aplikacích při použití XAML a rozhraní .NET Framework XAML Services API.  
  
## <a name="untrusted-xaml-in-applications"></a>Nedůvěryhodné XAML v aplikacích  
 V nejvíce obecném smyslu tento pojem nedůvěryhodné XAML je jakýkoli zdroj XAML, který aplikace nejsou výslovně zahrnout nebo generování.  
  
 XAML, který je zkompilován nebo uložené jako `resx`– typ prostředku v rámci důvěryhodné a podepsané sestavení není ze své podstaty nedůvěryhodný. XAML může důvěřovat míře důvěryhodnosti sestavení jako celek. Ve většině případů se pouze důvěryhodnosti aspektů volný XAML, který je zdroje XAML, který můžete načíst z datového proudu nebo jiné vstupně-výstupních operací. Volný XAML není konkrétní komponenta nebo funkce aplikačního modelu nasazení a balení infrastrukturu. Sestavení však může implementovat chování, které zahrnuje načtení volný XAML.  
  
 Pro nedůvěryhodné XAML, můžete by měly zpracovávat je obecně stejná jako by šlo nedůvěryhodného kódu. Pomocí izolace (sandbox) nebo jiné metaphors pravděpodobně nedůvěryhodné XAML zabránit v přístupu k důvěryhodným kódem.  
  
 Povaha funkce XAML poskytuje XAML práva k vytvoření objektů a nastavte jejich vlastnosti. Tyto možnosti zahrnují také přístup k převaděče typů, mapování a přístup k sestavení v aplikační doméně, pomocí rozšíření značek, `x:Code` bloky a tak dále.  
  
 Kromě možnosti úrovni jazyka XAML slouží k definici uživatelského rozhraní v mnoha technologií. Načítání nedůvěryhodné XAML může znamenat načtení škodlivých falšováním identity uživatelského rozhraní.  
  
## <a name="sharing-context-between-readers-and-writers"></a>Sdílení kontextu mezi čtečky a zapisovače  
 Architektura rozhraní .NET Framework XAML Services XAML čtečky a zapisovače XAML často vyžaduje sdílení XAML čtečky zapisovač XAML nebo sdílené kontext schématu XAML. Sdílení objekty nebo kontexty může být vyžadováno, pokud vytváříte logiky smyčky uzlu XAML nebo poskytnutí vlastní Uložit cestu. By neměly sdílet XAML čtečky instancí, jiný než výchozí kontext schématu XAML nebo nastavení pro čtení/zápis třídy XAML mezi důvěryhodné a nedůvěryhodné kódu.  
  
 Většina scénářů a operace, které zahrnují objektu XAML zápis pro typ na základě CLR zálohování můžete použít jenom výchozí kontext schématu XAML. Výchozí kontext schématu XAML nezahrnuje explicitně nastavení, které by mohly ohrozit úplný vztah důvěryhodnosti. Je tedy bezpečně sdílet kontext mezi důvěryhodné a nedůvěryhodné součásti čtení/zápis XAML. Pokud to uděláte, je však stále osvědčeným postupem je ponechat takové čtečky a zapisovače samostatné <xref:System.AppDomain> oborů s jedním z nich speciálně určené/řešeními v izolovaném prostoru pro částečnou důvěryhodností.  
  
## <a name="xaml-namespaces-and-assembly-trust"></a>Obory názvů XAML a sestavení důvěryhodnosti  
 Základní syntaxe nekvalifikovaného a definice interpretace vlastní mapování oboru názvů XAML do sestavení XAML nerozlišuje mezi důvěryhodné a nedůvěryhodné sestavení jako načteno do domény aplikace. Proto je technicky možné nedůvěryhodného sestavení zfalšovat mapování oboru názvů XAML určené důvěryhodná sestavení a zachycení deklarovanému objektu XAML zdroje a informace o vlastnosti. Pokud máte požadavky na zabezpečení, abyste předešli této situaci vaše zamýšlený mapování oboru názvů XAML je třeba pomocí jedné z následujících postupů:  
  
-   Použijte plně kvalifikovaný název s silný název v žádné mapování oboru názvů XAML provedené při vaší aplikace XAML.  
  
-   Omezit mapování na pevnou sadu referenčních sestavení tak, že vytváří konkrétní sestavení <xref:System.Xaml.XamlSchemaContext> pro vaše XAML čtečky a XAML objektu zapisovače. Viz <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.  
  
## <a name="xaml-type-mapping-and-type-system-access"></a>Mapování typů XAML a přístup k systému typu  
 XAML podporuje svůj vlastní typ systém, který se ve spoustě ohledů je partnera, který způsob implementace CLR systému základní typ CLR. Však pro některé aspekty typ povědomí, kde provádíte rozhodnutí o důvěryhodnosti o typu na základě jeho typu informací, by měl odložit na informace o typu v prostředí CLR typy zálohování. Je to proto, že některé konkrétní možnosti vytváření sestav typu systému XAML jsou ponechány otevřené jako virtuální metody a nejsou proto plně pod kontrolou původní implementace rozhraní .NET Framework XAML Services. Těmto rozšiřujícím bodům existovat, protože systém typů XAML je možné rozšířit tak, aby odpovídaly rozšiřitelnosti XAML samotného a možná alternativní strategii mapování typů a výchozí implementace podporou modulu CLR a výchozí kontext schématu XAML. Další informace najdete v tématu poznámky ke konkrétní na některé z vlastností <xref:System.Xaml.XamlType> a <xref:System.Xaml.XamlMember>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Xaml.Permissions.XamlAccessLevel>
