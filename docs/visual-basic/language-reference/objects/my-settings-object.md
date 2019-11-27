---
title: My.Settings – objekt
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 9560a51332ea596d4cf2228f1e07c158a0457ece
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350362"
---
# <a name="mysettings-object"></a>My.Settings – objekt
Poskytuje vlastnosti a metody pro přístup k nastavení aplikace.  
  
## <a name="remarks"></a>Poznámky  
 Objekt `My.Settings` poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládat a načítat nastavení vlastností a další informace pro vaši aplikaci. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Vlastnosti  
 Vlastnosti objektu `My.Settings` poskytují přístup k nastavení vaší aplikace. Chcete-li přidat nebo odebrat nastavení, použijte **Návrháře nastavení**.  
  
 Každé nastavení má **název**, **typ**, **Rozsah**a **hodnotu**a tato nastavení určují, jak se vlastnost pro přístup jednotlivých nastavení zobrazí v objektu `My.Settings`:  
  
- **Název** Určuje název vlastnosti.  
  
- **Typ** určuje typ vlastnosti.  
  
- **Scope** určuje, zda je vlastnost určena pouze pro čtení. Pokud je hodnota **aplikace**, vlastnost je jen pro čtení; Pokud je hodnota **uživatel**, vlastnost je určena pro čtení i zápis.  
  
- **Hodnota** je výchozí hodnota vlastnosti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|---|---|  
|`Reload`|Znovu načte uživatelská nastavení z naposledy uložených hodnot.|  
|`Save`|Uloží aktuální nastavení uživatele.|  
  
 Objekt `My.Settings` také poskytuje pokročilé vlastnosti a metody děděné z třídy <xref:System.Configuration.ApplicationSettingsBase>.  
  
## <a name="tasks"></a>Úlohy  
 V následující tabulce jsou uvedeny příklady úloh týkajících se `My.Settings` objektu.  
  
|Do|Další informace naleznete v tématu|  
|---|---|  
|Čtení nastavení aplikace|[Postupy: čtení nastavení aplikace v Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Změna uživatelského nastavení|[Postupy: Změna uživatelského nastavení v Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Zachovat uživatelská nastavení|[Postupy: zachování uživatelských nastavení v Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Vytvořit mřížku vlastností pro uživatelská nastavení|[Postupy: vytváření mřížek vlastností pro uživatelská nastavení v Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se zobrazí hodnota nastavení `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Aby tento příklad fungoval, musí mít aplikace `Nickname` nastavení typu `String`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Configuration.ApplicationSettingsBase>
- [Postupy: čtení nastavení aplikace v Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Postupy: Změna uživatelského nastavení v Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Postupy: zachování uživatelských nastavení v Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Postupy: vytváření mřížek vlastností pro uživatelská nastavení v Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
