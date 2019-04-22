---
title: My.Settings – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: a962f7cce961b1ee6829702a6815ba02c534efb4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840364"
---
# <a name="mysettings-object"></a>My.Settings – objekt
Poskytuje vlastnosti a metody pro přístup k nastavení aplikace.  
  
## <a name="remarks"></a>Poznámky  
 `My.Settings` Objekt poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládat a načítat nastavení vlastností a další informace pro vaši aplikaci. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Vlastnosti  
 Vlastnosti `My.Settings` objekt poskytnout přístup k nastavení aplikace. Chcete-li přidat nebo odebrat nastavení, použijte **návrháře nastavení**.  
  
 Každé nastavení má **název**, **typ**, **oboru**, a **hodnota**, a tato nastavení určují, jak vlastnost, která má přístup ke každé nastavení Zobrazí se v `My.Settings` objektu:  
  
-   **Název** Určuje název vlastnosti.  
  
-   **Typ** Určuje typ vlastnosti.  
  
-   **Obor** značí, zda je vlastnost jen pro čtení. Pokud je hodnota **aplikace**, vlastnost je jen pro čtení; Pokud je hodnota **uživatele**, je vlastnost pro čtení i zápis.  
  
-   **Hodnota** je výchozí hodnota vlastnosti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|---|---|  
|`Reload`|Znovu načte nastavení uživatele z poslední uložené hodnoty.|  
|`Save`|Uloží aktuální nastavení uživatele.|  
  
 `My.Settings` Objekt poskytuje také pokročilé vlastností a metod zděděných z <xref:System.Configuration.ApplicationSettingsBase> třídy.  
  
## <a name="tasks"></a>Úkoly  
 Následující tabulka uvádí příklady úloh týkajících `My.Settings` objektu.  
  
|Chcete-li|Další informace naleznete v tématu|  
|---|---|  
|Čtení nastavení aplikace|[Postupy: Čtení nastavení aplikace v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Změna uživatelského nastavení|[Postupy: Změna uživatelského nastavení v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Zachování uživatelského nastavení|[Postupy: Zachování uživatelského nastavení v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Vytvořit mřížku vlastností pro uživatelská nastavení|[Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Příklad  
 Tento příklad zobrazuje hodnotu `Nickname` nastavení.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Pro tento příklad fungoval, musí mít vaše aplikace `Nickname` typu nastavení `String`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Configuration.ApplicationSettingsBase>
- [Postupy: Čtení nastavení aplikace v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Postupy: Změna uživatelského nastavení v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Postupy: Zachování uživatelského nastavení v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
