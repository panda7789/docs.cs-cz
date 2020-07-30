---
title: Interoperabilita – Průvodce programováním v C#
description: Interoperabilita podporuje nespravovaný kód vedle kódu, který běží v modulu CLR (Common Language Runtime). Pomocí těchto zdrojů můžete pochopit možnosti spolupráce.
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: d85eb51107d50e023270fcbe1ef6e08a7788ae78
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302968"
---
# <a name="interoperability-c-programming-guide"></a>Interoperabilita (Průvodce programováním v C#)

Interoperabilita umožňuje zachovat a využít stávající investice do nespravovaného kódu. Kód, který se spouští pod kontrolou modulu CLR (Common Language Runtime), se nazývá *spravovaný kód*a kód, který se spouští mimo modul CLR, se nazývá *nespravovaný kód*. Příklady nespravovaného kódu jsou komponenty COM, COM+, C++, komponenty ActiveX a rozhraní Microsoft Windows API.  
  
.NET umožňuje vzájemnou funkční spolupráci s nespravovaným kódem prostřednictvím služeb vyvolání platformy, <xref:System.Runtime.InteropServices> oboru názvů, interoperability C++ a interoperability com (interoperabilita com).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled interoperability](./interoperability-overview.md)  
 Popisuje metody vzájemné spolupráce mezi spravovaným kódem jazyka C# a nespravovaným kódem.  
  
 [Jak získat přístup k objektům interoperability Office pomocí funkcí jazyka C#](./how-to-access-office-onterop-objects.md)  
 Popisuje funkce, které jsou představeny v jazyce Visual C# pro usnadnění programování v systému Office.  
  
 [Jak použít indexované vlastnosti při programování interoperability COM](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Popisuje způsob použití indexovaných vlastností pro přístup k vlastnostem modelu COM, které mají parametry.  
  
 [Jak použít vyvolání platformy k přehrání souboru WAV](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Popisuje způsob použití služeb vyvolání platformy k přehrání zvukového souboru. wav v operačním systému Windows.  
  
 [Návod: programování pro Office](./walkthrough-office-programming.md)  
 Ukazuje, jak vytvořit excelový sešit a wordový dokument, který obsahuje odkaz na sešit.  
  
 [Ukázka třídy COM](./example-com-class.md)  
 Ukazuje, jak vystavit třídu jazyka C# jako objekt modelu COM.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace najdete v tématu [základní koncepty](~/_csharplang/spec/unsafe-code.md) [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [Průvodce programováním v C#](../index.md)
- [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md)
- [Návod: programování pro Office](./walkthrough-office-programming.md)
