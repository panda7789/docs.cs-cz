---
title: My.Settings – objekt
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: c905ff85c8e9729dd4d6068f0d34f729962bbb57
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372398"
---
# <a name="mysettings-object"></a>My.Settings – objekt
Poskytuje vlastnosti a metody pro přístup k nastavení aplikace.  
  
## <a name="remarks"></a>Poznámky  
 `My.Settings`Objekt poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládat a načítat nastavení vlastností a další informace pro vaši aplikaci. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Vlastnosti  
 Vlastnosti `My.Settings` objektu poskytují přístup k nastavení vaší aplikace. Chcete-li přidat nebo odebrat nastavení, použijte **Návrháře nastavení**.  
  
 Každé nastavení má **název**, **typ**, **Rozsah**a **hodnotu**a tato nastavení určují, jak se vlastnost pro přístup jednotlivých nastavení zobrazí v `My.Settings` objektu:  
  
- **Název** Určuje název vlastnosti.  
  
- **Typ** určuje typ vlastnosti.  
  
- **Scope** určuje, zda je vlastnost určena pouze pro čtení. Pokud je hodnota **aplikace**, vlastnost je jen pro čtení; Pokud je hodnota **uživatel**, vlastnost je určena pro čtení i zápis.  
  
- **Hodnota** je výchozí hodnota vlastnosti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|---|---|  
|`Reload`|Znovu načte uživatelská nastavení z naposledy uložených hodnot.|  
|`Save`|Uloží aktuální nastavení uživatele.|  
  
 `My.Settings`Objekt také poskytuje pokročilé vlastnosti a metody děděné z <xref:System.Configuration.ApplicationSettingsBase> třídy.  
  
## <a name="tasks"></a>Úlohy  
 V následující tabulce jsou uvedeny příklady úloh týkajících se `My.Settings` objektu.  
  
|Akce|Seznamte se s |  
|---|---|  
|Čtení nastavení aplikace|[Postupy: Čtení nastavení aplikace v jazyce Visual Basic](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Změna uživatelského nastavení|[Postupy: Změna uživatelského nastavení v jazyce Visual Basic](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Zachovat uživatelská nastavení|[Postupy: Zachování uživatelského nastavení v jazyce Visual Basic](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Vytvořit mřížku vlastností pro uživatelská nastavení|[Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se zobrazí hodnota `Nickname` nastavení.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Aby tento příklad fungoval, musí mít vaše aplikace `Nickname` Nastavení typu `String` .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Configuration.ApplicationSettingsBase>
- [Postupy: Čtení nastavení aplikace v jazyce Visual Basic](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Postupy: Změna uživatelského nastavení v jazyce Visual Basic](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Postupy: Zachování uživatelského nastavení v jazyce Visual Basic](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
