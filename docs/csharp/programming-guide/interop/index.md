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
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925633"
---
# <a name="interoperability-c-programming-guide"></a>Interoperabilita (Průvodce programováním v C#)
Interoperabilita umožňuje zachovat a využít stávající investice do nespravovaného kódu. Je volána kód, který běží v rámci ovládacího prvku modulu common language runtime (CLR) *spravovaného kódu*, a je volána kód, který běží mimo rámec platformy CLR *nespravovaný kód*. COM, modelu COM +, komponenty C++, součásti ActiveX a rozhraní Microsoft Win32 API jsou příkladem nespravovaného kódu.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Umožňuje vzájemná funkční spolupráce s nespravovaným kódem prostřednictvím platformy vyvolat služby, <xref:System.Runtime.InteropServices> obor názvů, vzájemná funkční spolupráce jazyka C++ a vzájemná funkční spolupráce modelu COM (komunikace s objekty COM).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled interoperability](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 Popisuje metody pro spolupráci mezi kód jazyka C# spravovaného a nespravovaného kódu.  
  
 [Postupy: Přístup k objektům Interop sady Office pomocí funkcí Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 Popisuje funkce, které se zavedly v jazyce Visual C# k usnadnění programování pro Office.  
  
 [Postupy: Použití indexovaných vlastností při programování zprostředkovatele komunikace s objekty COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Popisuje, jak používat indexované vlastnosti pro přístup k vlastnostem modelu COM, které mají parametry.  
  
 [Postupy: Použití vyvolání platformy pro přehrání souboru wave](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Popisuje, jak používat platformu vyvolání služby k přehrání zvukového souboru WAV v operačním systému Windows.  
  
 [Postupy: Programování pro systém Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 Ukazuje, jak vytvořit Excelový sešit a dokument aplikace Word, který obsahuje odkaz na sešit.  
  
 [Ukázka třídy COM](../../../csharp/programming-guide/interop/example-com-class.md)  
 Ukazuje, jak vystavit třída jazyka C# jako objekt modelu COM.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Spolupráce s nespravovaným kódem](../../../../docs/framework/interop/index.md)  
 [Postupy: Programování pro systém Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
