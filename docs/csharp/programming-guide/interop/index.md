---
title: Průvodce programováním v jazyce Interoperability – C#
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 3a70d2ae077552bab536e96367cab0fda1661310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75712049"
---
# <a name="interoperability-c-programming-guide"></a>Interoperabilita (Průvodce programováním v C#)
Interoperabilita umožňuje zachovat a využít stávající investice do nespravovaného kódu. Kód, který běží pod kontrolou clr (COMMON Language Runtime), se nazývá *spravovaný kód*a kód, který běží mimo CLR, se nazývá *nespravovaný kód*. Com, COM+, C++ komponenty, komponenty ActiveX a rozhraní Microsoft Windows API jsou příklady nespravovaného kódu.  
  
 Rozhraní .NET Framework umožňuje interoperabilitu s <xref:System.Runtime.InteropServices> nespravovaným kódem prostřednictvím služeb vyvolání platformy, oboru názvů, interoperability jazyka C++ a interoperability modelu COM (interop modelu COM).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled interoperability](./interoperability-overview.md)  
 Popisuje metody pro vzájemné propojení mezi spravovaným kódem jazyka C# a nespravovaným kódem.  
  
 [Jak získat přístup k objektům interoperability Office pomocí funkcí jazyka C#](./how-to-access-office-onterop-objects.md)  
 Popisuje funkce, které jsou zavedeny v jazyce Visual C# pro usnadnění programování sady Office.  
  
 [Jak použít indexované vlastnosti při programování interoperability COM](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Popisuje použití indexovaných vlastností pro přístup k vlastnostem com, které mají parametry.  
  
 [Jak použít vyvolání platformy k přehrání souboru WAV](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Popisuje způsob, jak pomocí služby vyvolání platformy přehrát zvukový soubor WAV v operačním systému Windows.  
  
 [Návod: Programování v Office](./walkthrough-office-programming.md)  
 Ukazuje, jak vytvořit excelový sešit a wordový dokument obsahující odkaz na sešit.  
  
 [Ukázka třídy COM](./example-com-class.md)  
 Ukazuje, jak vystavit třídu C# jako objekt COM.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [Programovací příručka jazyka C#](../index.md)
- [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md)
- [Návod: Programování v Office](./walkthrough-office-programming.md)
