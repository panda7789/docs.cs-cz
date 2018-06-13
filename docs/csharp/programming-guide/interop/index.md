---
title: Interoperabilita (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: e854c51bd80809b92bb538475a407422b2eba7c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332878"
---
# <a name="interoperability-c-programming-guide"></a>Interoperabilita (Průvodce programováním v C#)
Vzájemná funkční spolupráce umožňuje zachovat a využít existující investice v nespravovaném kódu. Kód, který běží pod kontrolou common language runtime (CLR) se nazývá *spravovaného kódu*, a kód, který je spuštěn mimo modulu CLR se nazývá *nespravovaného kódu*. COM, COM +, C++ komponent, součásti ActiveX a Microsoft Win32 API jsou příklady nespravovaného kódu.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Umožňuje Interoperabilita s nespravovaným kódem prostřednictvím platformy vyvolání služby, <xref:System.Runtime.InteropServices> obor názvů, interoperabilita C++ a interoperabilita modelů COM (spoluprací COM).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled interoperability](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 Popisuje metody pro spolupráci mezi C# spravovaný kód a nespravovaného kódu.  
  
 [Postupy: Přístup k objektům Interop sady Office pomocí funkcí Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 Popisuje funkce, které jsou zavedené v jazyce Visual C# pro usnadnění programování pro Office.  
  
 [Postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Popisuje, jak používat indexované vlastnosti pro přístup COM vlastnosti, které mají parametry.  
  
 [Postupy: Použití vyvolání platformy pro přehrání souboru wave](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Popisuje způsob použití platformy vyvolání služby k přehrání zvukového souboru ve formátu WAV operačního systému Windows.  
  
 [Návod: Programování pro Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 Ukazuje, jak vytvořit sešit aplikace Excel a Word dokumentu, který obsahuje odkaz na sešitu.  
  
 [Ukázka třídy COM](../../../csharp/programming-guide/interop/example-com-class.md)  
 Ukazuje, jak vystavit třída C# jako objekt COM.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Spolupráce s nespravovaným kódem](../../../../docs/framework/interop/index.md)  
 [Návod: Programování pro Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
