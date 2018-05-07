---
title: 'Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: c03e7c6138633287506ff01128a1e2acb321b02d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic
Můžete vytvořit mřížku vlastností pro uživatelská nastavení naplněním <xref:System.Windows.Forms.PropertyGrid> ovládacího prvku pomocí vlastnosti uživatelského nastavení `My.Settings` objektu.  
  
> [!NOTE]
>  Aby tento příklad fungoval musí mít vaše aplikace nastavené uživatelské nastavení. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 `My.Settings` Objekt zpřístupňuje každé nastavení vlastnosti. Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení. Toto nastavení **oboru** Určuje, zda je vlastnost jen pro čtení; vlastnost pro **aplikace**-oboru nastavení je jen pro čtení, při vlastnost pro **uživatele**-oboru nastavení je pro čtení a zápis. Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Nejde změnit nebo uložit hodnoty nastavení aplikace za běhu. Nastavení aplikace lze změnit pouze při vytváření aplikace (pomocí **Návrhář projektu**) nebo úpravou konfiguračního souboru aplikace. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Tento příklad používá <xref:System.Windows.Forms.PropertyGrid> ovládací prvek pro přístup k vlastnostem uživatelského nastavení `My.Settings` objektu. Ve výchozím nastavení <xref:System.Windows.Forms.PropertyGrid> zobrazuje všechny vlastnosti `My.Settings` objektu. Ale mít vlastnosti uživatelského nastavení <xref:System.Configuration.UserScopedSettingAttribute> atribut. Tento příklad nastaví <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> vlastnost <xref:System.Windows.Forms.PropertyGrid> k <xref:System.Configuration.UserScopedSettingAttribute> k zobrazení pouze vlastnosti uživatelského nastavení.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Chcete-li přidat mřížku vlastností nastavení uživatele  
  
1.  Přidat **PropertyGrid** řídit z **sada nástrojů** na návrhovou plochu pro vaši aplikaci, předpokládá, že zde `Form1`.  
  
     Výchozí název ovládacího prvku mřížky vlastnost je `PropertyGrid1`.  
  
2.  Dvakrát klikněte na plochu návrháře pro `Form1` otevřete kód pro obslužnou rutinu události načtení formuláře.  
  
3.  Nastavte `My.Settings` objektu jako vybraný objekt pro mřížku vlastností.  
  
     [!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_1.vb)]  
  
4.  Nakonfigurujte mřížku vlastností zobrazí pouze nastavení uživatele.  
  
     [!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_2.vb)]  
  
    > [!NOTE]
    >  Chcete-li zobrazit pouze nastavení oboru aplikace, použijte <xref:System.Configuration.ApplicationScopedSettingAttribute> atribut místo <xref:System.Configuration.UserScopedSettingAttribute>.  
  
## <a name="robust-programming"></a>Robustní programování  
 Při vypnutí aplikace, aplikace uloží uživatelská nastavení. Chcete-li uložit nastavení okamžitě, zavolejte `My.Settings.Save` metoda. Další informace najdete v tématu [postupy: zachování uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Viz také  
 [Objekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Postupy: čtení nastavení aplikace v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [Postupy: Změna uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [Postupy: zachovaly uživatelská nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
