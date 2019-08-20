---
title: Příklad třídy COM – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 461d5a2afb197596c1c52daeeca0583b7b5e9693
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589137"
---
# <a name="example-com-class-c-programming-guide"></a>Ukázka třídy COM (Průvodce programováním v C#)
Následuje příklad třídy, kterou byste vystavili jako objekt modelu COM. Po umístění tohoto kódu do souboru. cs a jeho přidání do projektu nastavte vlastnost **Register pro zprostředkovatele komunikace s objekty COM** na **hodnotu true**. Další informace najdete v tématu [jak: Registrovat komponentu pro zprostředkovatele komunikace s](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100))objekty com.
  
 Vystavení C# vizuálních objektů modelu COM vyžaduje deklaraci rozhraní třídy, rozhraní události, je-li to požadováno, a samotné třídy. Členové třídy musí dodržovat tato pravidla, aby je bylo možné zobrazit v modelu COM:  
  
- Třída musí být veřejná.  
  
- Vlastnosti, metody a události musí být veřejné.  
  
- Vlastnosti a metody musí být deklarovány v rozhraní třídy.  
  
- Události musí být deklarovány v rozhraní události.  
  
 Ostatní veřejné členy třídy, které nejsou deklarovány v těchto rozhraních, nebudou v modelu COM viditelné, ale budou viditelné pro ostatní objekty .NET Framework.  
  
 Chcete-li vystavit vlastnosti a metody modelu COM, je nutné je deklarovat v rozhraní třídy a označit `DispId` je atributem a implementovat je do třídy. Pořadí, ve kterém jsou členy deklarovány v rozhraní, je pořadí použité pro model COM vtable.  
  
 Chcete-li zobrazit události z vaší třídy, je nutné je deklarovat v rozhraní události a označit je `DispId` atributem. Třída by neměla implementovat toto rozhraní.  
  
 Třída implementuje rozhraní třídy; může implementovat více než jedno rozhraní, ale první implementace bude výchozím rozhraním třídy. Sem Implementujte metody a vlastnosti vystavené objektu COM. Musí být označeny jako veřejné a musí odpovídat deklaracím v rozhraní třídy. Také deklarovat události vyvolané třídou zde. Musí být označeny jako veřejné a musí odpovídat deklaracím v rozhraní události.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Interoperabilita](./index.md)
- [Stránka Sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
