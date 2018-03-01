---
title: "My.Settings – objekt"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f744460f8ea6c6c7f5c8c5e1658bd357e910def
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="mysettings-object"></a>My.Settings – objekt
Poskytuje vlastnosti a metody pro přístup k nastavení aplikace.  
  
## <a name="remarks"></a>Poznámky  
 `My.Settings` Objekt poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládání a načítání nastavení vlastností a další informace pro vaši aplikaci. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Vlastnosti  
 Vlastnosti `My.Settings` objekt poskytnout přístup k nastavení aplikace. Chcete-li přidat nebo odebrat nastavení, použijte **nastavení návrháře**.  
  
 Každé nastavení má **název**, **typ**, **oboru**, a **hodnotu**, a tato nastavení určují, jak vlastnost, která má přístup každý nastavení Zobrazí se v `My.Settings` objektu:  
  
-   **Název** Určuje název vlastnosti.  
  
-   **Typ** Určuje typ vlastnosti.  
  
-   **Obor** označuje, zda je vlastnost jen pro čtení. Pokud je hodnota **aplikace**, vlastnost je jen pro čtení; Pokud je hodnota **uživatele**, vlastnost je pro čtení a zápis.  
  
-   **Hodnota** je výchozí hodnota vlastnosti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|---|---|  
|`Reload`|Znovu načte nastavení uživatele z poslední uložené hodnoty.|  
|`Save`|Uloží aktuální nastavení uživatele.|  
  
 `My.Settings` Objekt také poskytuje rozšířené vlastnosti a metody, dědí z <xref:System.Configuration.ApplicationSettingsBase> třídy.  
  
## <a name="tasks"></a>Úlohy  
 V následující tabulce jsou uvedeny příklady úkolů zahrnující `My.Settings` objektu.  
  
|Chcete-li|Další informace naleznete v tématu|  
|---|---|  
|Čtení nastavení aplikace|[Postupy: čtení nastavení aplikace v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Změňte uživatelské nastavení|[Postupy: Změna uživatelského nastavení v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Zachování uživatelského nastavení|[Postupy: zachovaly uživatelská nastavení v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Vytvořit mřížku vlastností pro nastavení uživatele|[Postupy: vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Příklad  
 Tento příklad zobrazuje hodnotu `Nickname` nastavení.  
  
 [!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]  
  
 Pro tento příklad fungoval, musí mít vaše aplikace `Nickname` typu nastavení `String`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Configuration.ApplicationSettingsBase>  
 [Postupy: čtení nastavení aplikace v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [Postupy: Změna uživatelského nastavení v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [Postupy: zachovaly uživatelská nastavení v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Postupy: vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
