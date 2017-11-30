---
title: "Ukázka třídy COM (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad14b414c037d38da55ce0ec82685b790cc46d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="example-com-class-c-programming-guide"></a>Ukázka třídy COM (Průvodce programováním v C#)
Následuje příklad třídu, která by vystavit jako objekt COM. Po tento kód je umístěn v souboru .cs a přidat do projektu, nastavte **zaregistrovat zprostředkovatel komunikace s objekty COM** vlastnost **True**. Další informace najdete v tématu [NIB: postupy: zaregistrovat součásti zprostředkovatel komunikace s objekty COM](http://msdn.microsoft.com/en-us/4de7d474-56e8-4027-994d-d47ca4725c5e).  
  
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Vzájemná funkční spolupráce](../../../csharp/programming-guide/interop/index.md)  
 [Stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
