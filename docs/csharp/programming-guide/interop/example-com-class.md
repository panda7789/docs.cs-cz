---
title: Ukázka třídy COM - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: d4ea445339057bc65c3597d30a46f46d58b6e696
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595533"
---
# <a name="example-com-class-c-programming-guide"></a>Ukázka třídy COM (Průvodce programováním v C#)
Následuje příklad třídy, která by vystavit jako objekt modelu COM. Poté, co tento kód byl umístěn v souboru .cs a přidány do projektu, nastavte **zaregistrovat pro interoperabilitu COM** vlastnost **True**. Další informace najdete v tématu [jak: Zaregistrovat pro interoperabilitu COM komponentu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).
  
 Vystavení objektů jazyka Visual C# do modelu COM vyžaduje deklarace třídy rozhraní, pokud se vyžaduje rozhraní události a vlastní třídy. Členy třídy musí dodržovat tato pravidla být viditelné modelu COM:  
  
- Třída musí být veřejné.  
  
- Vlastnosti, metody a události musí být veřejné.  
  
- Vlastnosti a metody musí být deklarována v rozhraní.  
  
- Události musí být deklarována v události rozhraní.  
  
 Jiné veřejné členy, které nejsou deklarovány v těchto rozhraní ve třídě nesmí být viditelné modelu COM, ale budou viditelné pro ostatní objekty rozhraní .NET Framework.  
  
 Vystavit vlastnosti a metody rozhraní COM, musí deklarovat na třídy rozhraní a označte je pomocí `DispId` atribut a je implementovat ve třídě. Pořadí, ve kterém jsou členy deklarované v rozhraní je v tom pořadí, používá pro COM vtable.  
  
 K vystavení události z vaší třídy, musí deklarovat v rozhraní události a označit je pomocí `DispId` atribut. Třída by neměla implementovat toto rozhraní.  
  
 Třída implementuje rozhraní třídy; To může implementovat více než jedno rozhraní, ale první implementace bude výchozí třída rozhraní. Implementace metody a vlastnosti vystavit rozhraní COM tady. Musí být označena jako veřejná a musí odpovídat deklarace třídy rozhraní. Také deklarujte události vyvolané službou třída tady. Musí být označena jako veřejná a musí odpovídat deklarace události rozhraní.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Interoperabilita](../../../csharp/programming-guide/interop/index.md)
- [Stránka Sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
