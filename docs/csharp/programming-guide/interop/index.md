---
title: Interoperabilita C# – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 896f89304289fd90c10da9aaa7ea15ada35ef8f7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589091"
---
# <a name="interoperability-c-programming-guide"></a>Interoperabilita (Průvodce programováním v C#)
Interoperabilita umožňuje zachovat a využít stávající investice do nespravovaného kódu. Kód, který se spouští pod kontrolou modulu CLR (Common Language Runtime), se nazývá *spravovaný kód*a kód, který se spouští mimo modul CLR, se nazývá nespravovaný *kód*. Příklady nespravovaného C++ kódu jsou com, com+, komponenty, komponenty ActiveX a rozhraní Microsoft Windows API.  
  
 .NET Framework umožňuje vzájemnou funkční spolupráci s nespravovaným kódem prostřednictvím služeb <xref:System.Runtime.InteropServices> vyvolání platformy C++ , oboru názvů, interoperability a interoperability modelu COM (komunikace s objekty com).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled interoperability](./interoperability-overview.md)  
 Popisuje metody vzájemné spolupráce mezi C# spravovaným kódem a nespravovaným kódem.  
  
 [Postupy: Přístup k objektům Interop Office pomocí C# vizuálních funkcí](./how-to-access-office-onterop-objects.md)  
 Popisuje funkce, které jsou představené C# ve vizuálu pro usnadnění programování pro Office.  
  
 [Postupy: Použití indexovaných vlastností v programování zprostředkovatele komunikace s objekty COM](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Popisuje způsob použití indexovaných vlastností pro přístup k vlastnostem modelu COM, které mají parametry.  
  
 [Postupy: Použít vyvolání platformy k přehrání souboru Wave](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Popisuje způsob použití služeb vyvolání platformy k přehrání zvukového souboru. wav v operačním systému Windows.  
  
 [Návod: Programování pro Office](./walkthrough-office-programming.md)  
 Ukazuje, jak vytvořit excelový sešit a wordový dokument, který obsahuje odkaz na sešit.  
  
 [Ukázka třídy COM](./example-com-class.md)  
 Ukazuje, jak vystavit C# třídu jako objekt modelu COM.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace najdete v tématu [základní koncepty](~/_csharplang/spec/unsafe-code.md) ve [ C# specifikaci jazyka](../../language-reference/language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [Průvodce programováním v jazyce C#](../index.md)
- [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md)
- [Návod: Programování pro Office](./walkthrough-office-programming.md)
