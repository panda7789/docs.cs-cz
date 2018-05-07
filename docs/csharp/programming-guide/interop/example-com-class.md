---
title: Ukázka třídy COM (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 2dd1092d9c1f6bb7482c306339a3d7f6684940eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="example-com-class-c-programming-guide"></a>Ukázka třídy COM (Průvodce programováním v C#)
Následuje příklad třídu, která by vystavit jako objekt COM. Po tento kód je umístěn v souboru .cs a přidat do projektu, nastavte **zaregistrovat zprostředkovatel komunikace s objekty COM** vlastnost **True**. Další informace najdete v tématu [NIB: postupy: zaregistrovat součásti zprostředkovatel komunikace s objekty COM](http://msdn.microsoft.com/library/4de7d474-56e8-4027-994d-d47ca4725c5e).  
  
 Vystavení objektů jazyka Visual C# do modelu COM vyžaduje deklarování třídy rozhraní, rozhraní události v případě potřeby a vlastní třídy. Členy třídy nutné postupovat podle těchto pravidel být viditelné modelu COM:  
  
-   Třída musí být veřejné.  
  
-   Vlastnosti, metod a události musí být veřejné.  
  
-   Vlastnosti a metody musí být deklarován v rozhraní třídy.  
  
-   Události musí být deklarován události rozhraní.  
  
 Jiné veřejné členy ve třídě, které nejsou deklarované v těchto rozhraní se nezobrazí COM, ale nebudou se viditelné pro jiné objekty rozhraní .NET Framework.  
  
 Která zveřejňuje vlastnosti a metody do modelu COM, musí deklarovat je v rozhraní třídy a označit je s `DispId` atribut a jejich implementaci ve třídě. Pořadí, ve které jsou deklarované členy v rozhraní je v pořadí, použít pro COM vtable.  
  
 Ke zveřejnění události z vaší třídy, musí deklarovat je v rozhraní události a označit je pomocí `DispId` atribut. Třída nesmí toto rozhraní implementovat.  
  
 Třída implementuje rozhraní třídy; ho můžete implementovat více než jedno rozhraní, ale bude první implementace rozhraní výchozí třídy. Implementace metody a vlastnosti vystaven objektům modelu COM v tomto poli. Tyto musí být označen a deklarace v rozhraní třídy se musí shodovat. Události vyvolané třídou zde také deklarujte. Tyto musí být označen a deklarace v rozhraní události se musí shodovat.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Interoperabilita](../../../csharp/programming-guide/interop/index.md)  
 [Stránka Sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
