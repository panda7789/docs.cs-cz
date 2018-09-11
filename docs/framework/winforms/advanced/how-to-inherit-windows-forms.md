---
title: 'Postupy: Dědění formulářů Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: 275ae52a36ed9766e2569bd6c8ecdea78ea56e0b
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276285"
---
# <a name="how-to-inherit-windows-forms"></a>Postupy: Dědění formulářů Windows
Vytvoření nového formuláře Windows děděním z podkladové formuláře je šikovný způsob, jak duplikovat vynaloží veškeré úsilí bez nutnosti kontaktovat proces pokaždé, když chcete, aby zcela opětovné vytvoření formuláře.  
  
 Další informace o dědění formulářů pomocí času návrhu **výběr dědičnosti** dialogové okno a tom, jak vizuálně rozlišovat mezi úrovněmi zabezpečení zděděné ovládacích prvků naleznete v tématu [postupy: dědění formulářů pomocí Dialogové okno Výběr dědičnosti](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).  
  
 **Poznámka:** aby bylo možné zdědit z formuláře, soubor nebo obor názvů obsahující, které tvoří musí sestavené do spustitelného souboru nebo knihovny DLL. Sestavte projekt, zvolte **sestavení** z **sestavení** nabídky. Odkaz na obor názvů navíc musí přidat na třídu, která dědí formuláře. Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-inherit-a-form-programmatically"></a>Dědění formuláře prostřednictvím kódu programu  
  
1.  Ve své třídě přidejte odkaz na obor názvů obsahující formulář, do kterého chcete dědí.  
  
2.  V definici třídy přidejte odkaz na formulář dědí. Odkaz na by měly zahrnovat obor názvů obsahující formulář, následovaných tečkou, pak název základní samotný formulář.  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 Při dědění formulářů, mějte na paměti, mohou se vyskytnout problémy z hlediska obslužné rutiny událostí volána dvakrát, protože se zpracovává každé události základní třídy a zděděná třída. Další informace o tom, jak tomuto problému vyhnout, naleznete v tématu [řešení potíží s zděděné obslužných rutin událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Inherits](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [Příkaz Imports (obor názvů a typ .NET)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [using](~/docs/csharp/language-reference/keywords/using.md)  
 [Účinky úpravy vzhledu základního formuláře](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [Vizuální dědění modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
