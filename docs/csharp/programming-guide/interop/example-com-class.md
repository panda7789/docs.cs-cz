---
title: Příklad třídy COM – Průvodce programováním v C#
description: Přečtěte si, jak vystavit třídu jako objekt modelu COM v jazyce C#. Tento příklad přidá kód do souboru. cs do projektu a nastaví registraci pro vlastnost Interop modelu COM.
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 4ea66ba26595c5bae2e579d1cc85c4b0d58616df
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303033"
---
# <a name="example-com-class-c-programming-guide"></a>Ukázka třídy COM (Průvodce programováním v C#)
Následuje příklad třídy, kterou byste vystavili jako objekt modelu COM. Po umístění tohoto kódu do souboru. cs a jeho přidání do projektu nastavte vlastnost **Register pro zprostředkovatele komunikace s objekty COM** na **hodnotu true**. Další informace najdete v tématu [Postup: registrace komponenty pro zprostředkovatele komunikace s objekty COM](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).
  
 Vystavení objektů jazyka Visual C# pro model COM vyžaduje deklaraci rozhraní třídy, rozhraní události, pokud je požadováno, a samotnou třídu. Členové třídy musí dodržovat tato pravidla, aby je bylo možné zobrazit v modelu COM:  
  
- Třída musí být veřejná.  
  
- Vlastnosti, metody a události musí být veřejné.  
  
- Vlastnosti a metody musí být deklarovány v rozhraní třídy.  
  
- Události musí být deklarovány v rozhraní události.  
  
 Ostatní veřejné členy třídy, které nejsou deklarovány v těchto rozhraních, nebudou v modelu COM viditelné, ale budou viditelné pro jiné objekty .NET.  
  
 Chcete-li vystavit vlastnosti a metody modelu COM, je nutné je deklarovat v rozhraní třídy a označit je `DispId` atributem a implementovat je do třídy. Pořadí, ve kterém jsou členy deklarovány v rozhraní, je pořadí použité pro model COM vtable.  
  
 Chcete-li zobrazit události z vaší třídy, je nutné je deklarovat v rozhraní události a označit je `DispId` atributem. Třída by neměla implementovat toto rozhraní.  
  
 Třída implementuje rozhraní třídy; může implementovat více než jedno rozhraní, ale první implementace bude výchozím rozhraním třídy. Sem Implementujte metody a vlastnosti vystavené objektu COM. Musí být označeny jako veřejné a musí odpovídat deklaracím v rozhraní třídy. Také deklarovat události vyvolané třídou zde. Musí být označeny jako veřejné a musí odpovídat deklaracím v rozhraní události.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Vzájemná funkční spolupráce](./index.md)
- [Stránka Sestavení, návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
