---
title: Přehled časových pásem
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], about time zones
- transition time [.NET Framework]
- TimeZoneInfo class, about TimeZoneInfo class
- time zones [.NET Framework], creating
- invalid time [.NET Framework]
- fixed rule [.NET Framework]
- ambiguous time [.NET Framework]
- floating rule [.NET Framework]
- daylight saving time [.NET Framework]
- adjustment rule [.NET Framework]
- time zones [.NET Framework], terminology
ms.assetid: c4b7ed01-5e38-4959-a3b6-ef9765d6ccf1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5fa4376cdb0496cfd25f4764257c4f3afbc7268
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54697046"
---
# <a name="time-zone-overview"></a>Přehled časových pásem

<xref:System.TimeZoneInfo> Třída usnadňuje vytváření aplikací pracujících s časové pásmo. <xref:System.TimeZone> Třídy podporuje práci s místním časovém pásmu a koordinovaný univerzální čas (UTC). <xref:System.TimeZoneInfo> Třída podporuje obě tyto zóny, stejně jako časové pásmo, které informace je předdefinovaná v registru. Můžete také použít <xref:System.TimeZoneInfo> k definování vlastní časové pásmo, systém nemá žádné informace o.

## <a name="time-zone-essentials"></a>Časové pásmo essentials

Časové pásmo je geografické oblasti, ve kterém se používá stejnou dobu. Obvykle, ale ne vždy se sousední časových pásem jedné hodiny od sebe. Doba v některém z celého světa časových pásmech, může být vyjádřena jako posun od koordinovaného světového času (UTC).

Podporuje mnoho světových časových pásem letní čas. Letního času se snaží maximalizovat letního času hodin Posunutí vpřed času o jednu hodinu v spring nebo dřívější léto a vrátí normální (nebo standard) čas v pozdní letní nebo fall. Tyto změny do a z (běžný čas) jsou označovány jako pravidla úpravy.

Přechod z letní čas v určitém časovém pásmu a může být definován tak, že pevnou nebo plovoucí pravidlo úpravy. Pevné pravidlo úpravy nastaví do určitého data, na kterém dojde k přechodu do nebo z letní čas každý rok. Přechod z letního času na (běžný čas), který se nachází na 25. října každý rok se například řídí pevné pravidlo úpravy. Mnohem více běžné jsou plovoucí úprava pravidla, která nastaví určitý den konkrétní týdne v daném měsíci pro přechod do nebo z letního času. Například přechodu ze standardního času na letní čas, který se nachází na třetí neděli v březnu následuje plovoucí pravidlo úpravy.

Pro časová pásma, které podporují pravidla úpravy přechod z letního času a vytvoří dva druhy neobvyklé časy: Neplatný časech a nejednoznačných časových údajů. Neplatný čas je čas neexistující vytvořené přechodu ze standardního času na letní čas. Například, pokud nastane tento přechod v určitý den ve 2:00:00 a způsobí, že čas změny na 3:00 dop., v každém časovém intervalu mezi 2:00:00 and 2:59:99 A.M. je neplatný. Nejednoznačný čas je čas, který je možné mapovat na dva různé časy v jedné časové pásmo. Vytvoření přechodu ze letního času na (běžný čas). Například, pokud nastane tento přechod v určitý den ve 2:00:00 a způsobí, že čas změny na 1:00 dop., v každém časovém intervalu mezi 1:00 dop. and 1:59:99 A.M. může být interpretován jako standardní čas nebo letní čas.

## <a name="time-zone-terminology"></a>Terminologie časové pásmo

Následující tabulka definuje podmínky běžně používají při práci s časovými pásmy a vývoj aplikací s ohledem na časové pásmo.

| Termín            | Definice |
| --------------- | ---------- |
| Pravidlo úpravy | Pravidla, která definuje, dojde k přechodu ze standardního času na letní čas a obnovení z letního času na (běžný čas). Každé pravidlo úprav má počáteční a koncové datum, která definuje, kdy pravidlo je na místě (například nastavení je pravidlo na místě od 1. ledna 1986 do 31. prosince 2006), rozdílového (počet hodin, podle kterého standardní čas změny v důsledku použití th pravidlo úpravy e) a informace o konkrétní datum a čas, že přechody dojít během období úpravy. Pravidlo pevnou nebo plovoucí pravidlo, můžete postupovat podle přechodů. |
| Nejednoznačný čas  | Čas, který je možné mapovat na dva různé časy v jedné časové pásmo. K tomu dochází, když čas dojde k přenastavení zpět v čase, například při přechodu z časové pásmo letního času na jeho (běžný čas). Například, pokud nastane tento přechod v určitý den ve 2:00:00 a způsobí, že čas změny na 1:00 dop., v každém časovém intervalu mezi 1:00 dop. and 1:59:99 A.M. může být interpretován jako standardní čas nebo letní čas. |
| Pevné pravidlo      | Pravidlo úpravy, které nastaví konkrétní datum pro přechod do nebo z letního času. Přechod z letního času na (běžný čas), který se nachází na 25. října každý rok se například řídí pevné pravidlo úpravy. |
| Plovoucí pravidlo   | Pravidlo úpravy, které nastaví určitý den konkrétní týdne v daném měsíci pro přechod do nebo z letního času. Například přechodu ze standardního času na letní čas, který se nachází na třetí neděli v březnu následuje plovoucí pravidlo úpravy. |
| Neplatný čas    | Neexistující čas, který je přechodu ze standardního času na letní čas. K tomu dochází, když čas dojde k přenastavení vpřed v čase, například při přechodu na letní čas z časové pásmo (běžný čas). Například, pokud nastane tento přechod v určitý den ve 2:00:00 a způsobí, že čas změny na 3:00 dop., v každém časovém intervalu mezi 2:00:00 and 2:59:99 A.M. je neplatný. |
| Čas přechodu | Informace o určitém čase měnit, jako je změna z letní čas (běžný čas) nebo naopak, v určitém časovém pásmu. |

## <a name="time-zones-and-the-timezoneinfo-class"></a>Časová pásma a TimeZoneInfo – třída

V rozhraní .NET <xref:System.TimeZoneInfo> objekt představuje časové pásmo. <xref:System.TimeZoneInfo> Obsahuje třídy <xref:System.TimeZoneInfo.GetAdjustmentRules%2A> metodu, která vrací pole <xref:System.TimeZoneInfo.AdjustmentRule> objekty. Každý prvek toto pole obsahuje informace o přechodu do a z letního času pro určité časové období. (Pro časová pásma, které nepodporují letního času, metoda vrátí prázdné pole.) Každý <xref:System.TimeZoneInfo.AdjustmentRule> má objekt <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionStart%2A> a <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionEnd%2A> vlastnost, která definuje konkrétní datum a čas přechodu do a z letního času. <xref:System.TimeZoneInfo.TransitionTime.IsFixedDateRule%2A> Vlastnost určuje, zda je tento přechod pevnou nebo plovoucí.

.NET spoléhá na informace o časovém pásmu v operačním systému Windows k dispozici a uložen v registru. Vzhledem k počtu časové pásmo ne všechny existující časových pásem jsou reprezentovány v registru. Navíc protože registru je struktura, dynamická, předdefinovaná časová pásma lze přidat do nebo z něj odebrat. Nakonec registru nezbytně nemusí obsahovat historické časové pásmo data. Například ve Windows XP registr obsahuje data o pouze jedinou sadu úpravy časového pásma. Windows Vista podporuje dynamické časové pásmo dat, což znamená, že jeden časové pásmo může mít víc úpravy pravidla, které se vztahují na konkrétní intervaly let. Většina časová pásma, která jsou definována ve Windows Vista a podporují letního času však mít pouze jednu nebo dvě předdefinovaná pravidla úpravy.

Závislost <xref:System.TimeZoneInfo> třídu v registru znamená, že aplikace s ohledem na časové pásmo nemůže být určité, že konkrétní časové pásmo je definována v registru. Pokus o vytvoření instance konkrétní časové pásmo (jiné než místní časové pásmo a časovém pásmu, který představuje čas UTC) v důsledku toho by měl použít zpracování výjimek. Mělo by také poskytovat některé metody, které umožní aplikaci pokračovat, pokud požadovaný <xref:System.TimeZoneInfo> nelze vytvořit instanci objektu z registru.

Pro zpracování chybí požadované časové pásmo <xref:System.TimeZoneInfo> obsahuje třídy <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodu, která slouží k vytvoření vlastního časového pásma, které se nenacházejí v registru. Podrobnosti o vytvoření vlastní časové pásmo, naleznete v tématu [jak: Vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) a [jak: Vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md). Kromě toho můžete použít <xref:System.TimeZoneInfo.ToSerializedString%2A> metodu pro nově vytvořený časové pásmo převést na řetězec a uložte jej v úložišti dat (například databáze, do textového souboru, registru nebo prostředek aplikace). Pak můžete použít <xref:System.TimeZoneInfo.FromSerializedString%2A> způsobů, jak převést řetězec zpět <xref:System.TimeZoneInfo> objektu. Podrobnosti najdete v tématu [jak: Ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) a [jak: Obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

Protože každý časové pásmo se vyznačuje základní posun od času UTC a posun od času UTC, která odráží všechny existující pravidla úpravy, čas v jednom časovém pásmu můžete snadno převést na čas v jiném časovém pásmu. Pro tento účel <xref:System.TimeZoneInfo> objekt obsahuje několik metod pro převod, včetně:

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>, který převede na čas v požadovaném časovém pásmu UTC.

* <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>, která převede na čas v požadovaném časovém pásmu UTC.

* <xref:System.TimeZoneInfo.ConvertTime%2A>, která převede na čas v jednom časovém pásmu na čas v jiném časovém pásmu.

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>, který používá identifikátory časových pásem (místo <xref:System.TimeZoneInfo> objektů) jako parametry pro převod na čas v jednom časovém pásmu na čas v jiném časovém pásmu.

Podrobnosti o převádění časových údajů mezi časovými pásmy najdete v tématu [převádění časových údajů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md).

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
