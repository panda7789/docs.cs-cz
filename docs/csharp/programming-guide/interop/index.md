---
title: Interoperabilita C# – Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 3a70d2ae077552bab536e96367cab0fda1661310
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712049"
---
# <a name="interoperability-c-programming-guide"></a>Interoperabilita (Průvodce programováním v C#)
Interoperabilita umožňuje zachovat a využít stávající investice do nespravovaného kódu. Kód, který se spouští pod kontrolou modulu CLR (Common Language Runtime), se nazývá *spravovaný kód*a kód, který se spouští mimo modul CLR, se nazývá *nespravovaný kód*. Příklady nespravovaného C++ kódu jsou com, com+, komponenty, komponenty ActiveX a rozhraní Microsoft Windows API.  
  
 .NET Framework umožňuje vzájemnou funkční spolupráci s nespravovaným kódem prostřednictvím služeb vyvolání platformy, C++ <xref:System.Runtime.InteropServices> oboru názvů, interoperability a interoperability com (interoperabilita com).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled interoperability](./interoperability-overview.md)  
 Popisuje metody vzájemné spolupráce mezi C# spravovaným kódem a nespravovaným kódem.  
  
 [Přístup k objektům Interop sady Office pomocí C# funkcí](./how-to-access-office-onterop-objects.md)  
 Popisuje funkce, které jsou představené C# ve vizuálu pro usnadnění programování pro Office.  
  
 [Použití indexovaných vlastností v programování zprostředkovatele komunikace s objekty COM](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Popisuje způsob použití indexovaných vlastností pro přístup k vlastnostem modelu COM, které mají parametry.  
  
 [Jak použít vyvolání platformy k přehrání souboru WAV](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Popisuje způsob použití služeb vyvolání platformy k přehrání zvukového souboru. wav v operačním systému Windows.  
  
 [Návod: programování pro Office](./walkthrough-office-programming.md)  
 Ukazuje, jak vytvořit excelový sešit a wordový dokument, který obsahuje odkaz na sešit.  
  
 [Ukázka třídy COM](./example-com-class.md)  
 Ukazuje, jak vystavit C# třídu jako objekt modelu COM.  
  
## <a name="c-language-specification"></a>C# – jazyková specifikace  

Další informace najdete v tématu [základní koncepty](~/_csharplang/spec/unsafe-code.md) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [Průvodce programováním v jazyce C#](../index.md)
- [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md)
- [Návod: programování pro Office](./walkthrough-office-programming.md)
