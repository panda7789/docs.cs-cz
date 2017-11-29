---
title: "Postupy: Dědění formulářů Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e986c79887ad19c77761b5ce134e4a3d68200d1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-inherit-windows-forms"></a>Postupy: Dědění formulářů Windows
Vytvoření nové Windows Forms pomocí dědění z podkladové formuláře je užitečný způsob, jak duplicitní maximální úsilí bez průchodu přes proces pokaždé, když to vyžadují zcela nové vytvoření formuláře.  
  
 Další informace o dědění formulářů pomocí čas návrhu **výběr dědičnosti** dialogové okno a postup vizuálně rozlišit mezi úrovněmi zabezpečení zděděná ovládací prvky najdete v tématu [postupy: dědění formulářů pomocí Dialogové okno Výběr dědičnosti](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).  
  
 **Poznámka:** aby bylo možné zdědit z formuláře, soubor nebo obor názvů obsahující tato forma musí mít sestavily do spustitelného souboru nebo knihovny DLL. Pro sestavení projektu, zvolte **sestavení** z **sestavení** nabídky. Odkaz na obor názvů navíc musí přidat k třídě dědí formuláře. Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-inherit-a-form-programmatically"></a>Chcete-li zdědit formuláře prostřednictvím kódu programu  
  
1.  Ve třídě přidejte odkaz na obor názvů obsahující formulář, který chcete dědí.  
  
2.  V definici třídy přidejte odkaz na formulář dědění z. Obor názvů, který obsahuje formulář, následuje dobou, pak název základní formuláři samotnému by měla obsahovat odkaz na.  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 Při dědění formulářů, mějte na paměti, která mohou se vyskytnout potíže se s ohledem na obslužné rutiny událostí se volala dvakrát, protože každé události je zpracovanou základní třídy a zděděné třídy. Další informace o tom, jak zamezit tomuto problému najdete v tématu [řešení potíží s zděděná obslužné rutiny událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="see-also"></a>Viz také  
 [Inherits – příkaz](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [Imports – příkaz (Namespace .NET a typ)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [pomocí](~/docs/csharp/language-reference/keywords/using.md)  
 [Účinky úpravy vzhledu základního formuláře](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [Vizuální dědění Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
