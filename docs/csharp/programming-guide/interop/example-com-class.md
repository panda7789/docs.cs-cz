---
title: Příklad průvodce programováním třídy COM – C#
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 6af85d0314a44acbde0996cecbe6dad82cdcc8db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712075"
---
# <a name="example-com-class-c-programming-guide"></a>Ukázka třídy COM (Průvodce programováním v C#)
Následuje příklad třídy, kterou byste zpřístupnili jako objekt COM. Po umístění tohoto kódu do souboru .cs a přidání do projektu nastavte vlastnost **Register for COM Interop** na **hodnotu True**. Další informace naleznete v [tématu How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).
  
 Vystavení objektů Visual C# pro com vyžaduje deklarování rozhraní třídy, rozhraní událostí, pokud je požadováno, a samotnou třídu. Členové třídy musí dodržovat tato pravidla, aby byla viditelná pro koma:  
  
- Třída musí být veřejná.  
  
- Vlastnosti, metody a události musí být veřejné.  
  
- Vlastnosti a metody musí být deklarovány v rozhraní třídy.  
  
- Události musí být deklarovány v rozhraní události.  
  
 Ostatní veřejné členy ve třídě, které nejsou deklarovány v těchto rozhraních nebude viditelné pro COM, ale budou viditelné pro jiné objekty rozhraní .NET Framework.  
  
 Chcete-li zpřístupnit vlastnosti a metody com, musíte deklarovat je na rozhraní třídy a označit je atributem `DispId` a implementovat je ve třídě. Pořadí, ve kterém jsou členy deklarovány v rozhraní je pořadí používané pro vtable COM.  
  
 Chcete-li vystavit události z vaší třídy, musíte je `DispId` deklarovat na rozhraní událostí a označit je atributem. Třída by neměla implementovat toto rozhraní.  
  
 Třída implementuje rozhraní třídy; může implementovat více než jedno rozhraní, ale první implementace bude výchozí rozhraní třídy. Implementujte metody a vlastnosti vystavené com zde. Musí být označeny jako veřejné a musí odpovídat deklaracím v rozhraní třídy. Také deklarovat události vyvolané třídy zde. Musí být označeny jako veřejné a musí odpovídat deklaracím v rozhraní událostí.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Vzájemná funkční spolupráce](./index.md)
- [Stránka Sestavení, návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
