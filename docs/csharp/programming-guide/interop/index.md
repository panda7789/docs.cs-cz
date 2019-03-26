---
title: 'Vzájemná funkční spolupráce – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
  - COM interop
  - interoperability
  - 'platform invoke, accessing APIs with C#'
  - 'C# language, interoperability'
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
---
# <a name="interoperability-c-programming-guide"></a>Interoperabilita (Průvodce programováním v C#)
Interoperabilita umožňuje zachovat a využít stávající investice do nespravovaného kódu. Je volána kód, který běží v rámci ovládacího prvku modulu common language runtime (CLR) *spravovaného kódu*, a je volána kód, který běží mimo rámec platformy CLR *nespravovaný kód*. COM, modelu COM +, komponenty C++, součásti ActiveX a rozhraní API Microsoft Windows jsou příkladem nespravovaného kódu.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Umožňuje vzájemná funkční spolupráce s nespravovaným kódem prostřednictvím platformy vyvolat služby, <xref:System.Runtime.InteropServices> obor názvů, vzájemná funkční spolupráce jazyka C++ a vzájemná funkční spolupráce modelu COM (komunikace s objekty COM).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled interoperability](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 Popisuje metody pro spolupráci mezi kód jazyka C# spravovaného a nespravovaného kódu.  
  
 [Postupy: Přístup k objektům Interop sady Office pomocí Vizuálu C# funkce](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 Popisuje funkce, které se zavedly v jazyce Visual C# k usnadnění programování pro Office.  
  
 [Postupy: Použití indexovaných vlastností při programování vzájemné spolupráce COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Popisuje, jak používat indexované vlastnosti pro přístup k vlastnostem modelu COM, které mají parametry.  
  
 [Postupy: Použití vyvolání platformy pro přehrání souboru Wave](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Popisuje, jak používat platformu vyvolání služby k přehrání zvukového souboru WAV v operačním systému Windows.  
  
 [Návod: Programování pro systém Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 Ukazuje, jak vytvořit Excelový sešit a dokument aplikace Word, který obsahuje odkaz na sešit.  
  
 [Ukázka třídy COM](../../../csharp/programming-guide/interop/example-com-class.md)  
 Ukazuje, jak vystavit třída jazyka C# jako objekt modelu COM.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace najdete v tématu [základní koncepty](~/_csharplang/spec/unsafe-code.md) v [ C# specifikace jazyka](../../language-reference/language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Spolupráce s nespravovaným kódem](../../../../docs/framework/interop/index.md)
- [Návod: Programování pro systém Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
