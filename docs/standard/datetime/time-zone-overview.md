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
ms.openlocfilehash: 85483e4319b56c0df150558ce6c6a3878a6fa041
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578083"
---
# <a name="time-zone-overview"></a>Přehled časových pásem

<xref:System.TimeZoneInfo> Třída zjednodušuje vytváření aplikace využívající technologii časové pásmo. <xref:System.TimeZone> Třídy podporuje práci s místním časovém pásmu a koordinovaný světový čas (UTC). <xref:System.TimeZoneInfo> Třída podporuje obě tyto zóny, stejně jako jakýkoli časové pásmo, o které informace je předdefinovaná v registru. Můžete také použít <xref:System.TimeZoneInfo> definovat vlastní časové pásmo, systém nemá žádné informace o.

## <a name="time-zone-essentials"></a>Časové pásmo essentials

Časové pásmo je geografické oblasti, ve kterém se používá ve stejnou dobu. Obvykle, ale ne vždy jsou sousední časová pásma jednu hodinu od sebe. Čas ve všech časových pásem na světě může být vyjádřený jako posun od koordinovaného světového času (UTC).

Mnoho světových časových pásem podporuje letní čas. Letní čas snaží co letní čas přechodu o jednu hodinu v pružiny nebo časná letní čas dál a návrat na normální (nebo standardní) čas v na konci léta nebo patří. Tyto změny do a z (běžný čas) se označují jako pravidla úpravy.

Přechod z letní čas v určitém časovém pásmu a může být definováno pevná nebo plovoucí pravidlo úpravy. Pevné pravidlo úpravy nastaví do určitého data, ve kterém k přechodu do nebo z letní čas každý rok. Například přechod z letní čas (běžný čas), ke kterému dochází každý rok 25 následuje pevné pravidlo úpravy. Více běžné jsou plovoucí pravidla úpravy, které nastaví určitý den určitého týdne v určitém měsíci pro přechod do nebo z letní čas. Například přechod ze standardního času na letní čas, ke kterému dochází ve třetí neděli v březnu řeší plovoucí pravidlo úpravy.

Časová pásma, které podporují pravidla úpravy, přechod z letní čas a vytvoří dva druhy neobvyklé časy: Neplatný časy a nejednoznačných časových údajů. Neplatná doba je neexistující čas vytvořené ze standardního času přechodu na letní čas. Například, pokud dojde k tento přechod na určitý den ve 2:00:00 a příčiny času změnu 3:00 ráno, v každém časovém intervalu mezi 2:00:00 a 2:59:99 dop. je neplatný. Nejednoznačný čas je čas, který lze mapovat na dva různé časy v jediném časovém pásmu. Vytvoří přechod z letní čas (běžný čas). Například, pokud dojde k tento přechod na určitý den ve 2:00:00 a příčiny času změnu 1:00 ráno, v každém časovém intervalu mezi 1:00 ráno a 1:59:99 dop. jde interpretovat jako běžný čas nebo letní čas.

## <a name="time-zone-terminology"></a>Terminologie časových pásem

Následující tabulka definuje termíny běžně používané při práci s časovými pásmy a vývoj aplikace využívající technologii časové pásmo.

| Termín            | Definice |
| --------------- | ---------- |
| Pravidlo úpravy | Pravidlo, které definuje, dojde k přechodu na letní čas (běžný čas) a zpět z letního času na (běžný čas). Každé pravidlo úpravy má počáteční a koncové datum, která definuje, pokud je pravidlo v místě (například pravidlo úpravy je na místě od 1. ledna 1986, do 31. prosince 2006) rozdílová (množství času, podle kterého běžný čas změny v důsledku použití tý pravidlo úpravy e) a informace o určité datum a čas, který přechodů mají nastat během období úpravy. Přechody může následovat pevné pravidlo nebo plovoucí pravidlo. |
| Nejednoznačný čas  | Čas, který lze mapovat na dva různé časy v jediném časovém pásmu. K tomu dojde, při času hodin se upraví zpět v čase, například při přechodu z letního času časového pásma na jeho (běžný čas). Například, pokud dojde k tento přechod na určitý den ve 2:00:00 a příčiny času změnu 1:00 ráno, v každém časovém intervalu mezi 1:00 ráno a 1:59:99 dop. jde interpretovat jako běžný čas nebo letní čas. |
| Pevné pravidlo      | Pravidlo úpravy, které nastavuje konkrétní datum pro přechod do nebo z letní čas. Například přechod z letní čas (běžný čas), ke kterému dochází každý rok 25 následuje pevné pravidlo úpravy. |
| Plovoucí pravidlo   | Pravidlo úpravy nastaví určitý den určitého týdne v určitém měsíci pro přechod do nebo z letní čas. Například přechod ze standardního času na letní čas, ke kterému dochází ve třetí neděli v březnu řeší plovoucí pravidlo úpravy. |
| Neplatná doba    | Neexistující čas, který je artefakt ze standardního času přechodu na letní čas. K tomu dochází, když času hodin se upraví dál v průběhu času, například při přechodu na časové pásmo na letní čas. Například, pokud dojde k tento přechod na určitý den ve 2:00:00 a příčiny času změnu 3:00 ráno, v každém časovém intervalu mezi 2:00:00 a 2:59:99 dop. je neplatný. |
| Čas přechodu | Informace o určitém čase měnit, jako je změna z letní čas (běžný čas) nebo naopak, v určitém časovém pásmu. |

## <a name="time-zones-and-the-timezoneinfo-class"></a>Časová pásma a TimeZoneInfo – třída

V rozhraní .NET <xref:System.TimeZoneInfo> objekt představuje časové pásmo. <xref:System.TimeZoneInfo> Obsahuje třídy <xref:System.TimeZoneInfo.GetAdjustmentRules%2A> metodu, která vrátí pole <xref:System.TimeZoneInfo.AdjustmentRule> objekty. Každý prvek toto pole obsahuje informace o přechodu do a z letní čas pro určité časové období. (Časová pásma, které nepodporují letní čas, metoda vrátí prázdné pole.) Každý <xref:System.TimeZoneInfo.AdjustmentRule> objekt má <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionStart%2A> a <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionEnd%2A> vlastnost, která definuje konkrétní datum a čas přechodu do a z letní čas. <xref:System.TimeZoneInfo.TransitionTime.IsFixedDateRule%2A> Vlastnost označuje, zda je tento přechod pevný nebo plovoucí.

Rozhraní .NET spoléhá na informace o časovém pásmu poskytované operačním systémem Windows a uložen v registru. Vzhledem k počtu časové pásmo jsou reprezentovány ne všechny existující časových pásem v registru. Kromě toho registru je dynamická struktura, a proto předdefinovaná časová pásma lze přidat do nebo z něj odebrat. Nakonec registru nemusí obsahovat dat znamená, že historické časového pásma. V systému Windows XP například registr obsahuje data o pouze jedinou sadu úpravy časové pásmo. Windows Vista podporuje dynamické časové pásmo data, která znamená, že jeden časové pásmo může mít více pravidel úpravy, které platí pro konkrétní intervaly let. Většina časových pásem, které jsou definované v systému Windows Vista a podporují letního času však mít pouze jednu nebo dvě předdefinovaná pravidla úpravy.

Závislost <xref:System.TimeZoneInfo> třídy v registru znamená, že časová pásma si aplikace nemůže být určité, že konkrétní časové pásmo je definována v registru. Pokus o vytvoření instance konkrétní časové pásmo (jiné než časové pásmo, které představuje čas UTC nebo místního časového pásma) v důsledku toho by měl použít zpracování výjimek. Poskytuje rovněž některé metody, které umožní aplikaci pokračovat, pokud povinná <xref:System.TimeZoneInfo> nelze vytvořit instanci objektu z registru.

Pro zpracování chybějícího požadované časové pásmo <xref:System.TimeZoneInfo> obsahuje třídy <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodu, která slouží k vytvoření vlastního časového pásma, které se nenacházejí v registru. Informace o vytváření vlastního časového pásma naleznete v tématu [postupy: vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) a [postupy: vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md). Kromě toho můžete použít <xref:System.TimeZoneInfo.ToSerializedString%2A> metoda chcete převést na řetězec nově vytvořený časové pásmo a uložit ho v úložišti dat (například databáze, do textového souboru, registru nebo prostředek aplikace). Pak můžete použít <xref:System.TimeZoneInfo.FromSerializedString%2A> způsobů, jak tento řetězec převést zpět na <xref:System.TimeZoneInfo> objektu. Podrobnosti najdete v tématu [postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) a [postupy: obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

Protože každý časové pásmo je vyznačují podle základní posun od času UTC, a posun od času UTC, která odráží platná pravidla úpravy, čas v jednom časovém pásmu lze snadno převést na čas v jiném časovém pásmu. Pro tento účel <xref:System.TimeZoneInfo> objektu obsahuje několik metod pro převod, včetně:

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>, která převede čas v určené časové pásmo UTC.

* <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>, která převede čas ve určené časové pásmo UTC.

* <xref:System.TimeZoneInfo.ConvertTime%2A>, která převede čas v jednom časovém pásmu na čas v jiném časovém pásmu.

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>, který používá identifikátory časových pásem (místo <xref:System.TimeZoneInfo> objektů) jako parametry pro převod času v jednom časovém pásmu na čas v jiném časovém pásmu.

Podrobnosti na převádění časových údajů mezi časovými pásmy najdete v tématu [převádění časových údajů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md).

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
