---
title: 'Postupy: Vytváření mřížek vlastností pro nastavení uživatele'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: bed4e8a2b50f0115c3b8d9d6abf427df5f216388
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329615"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic

Mřížku vlastností pro uživatelské nastavení můžete vytvořit naplněním <xref:System.Windows.Forms.PropertyGrid> ovládacího prvku pomocí vlastností uživatelského nastavení `My.Settings` objektu.  
  
> [!NOTE]
> Aby tento příklad fungoval, musí mít vaše aplikace nastavené uživatelské nastavení. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 `My.Settings` Objekt zpřístupňuje každé nastavení jako vlastnost. Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení. **Rozsah** nastavení určuje, zda je vlastnost určena pouze pro čtení; vlastnost pro nastavení rozsahu **aplikace**je jen pro čtení a vlastnost pro nastavení rozsahu **uživatele**je pro čtení i zápis. Další informace najdete v tématu [objekt My. Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> V době běhu nemůžete změnit ani uložit hodnoty nastavení rozsahu aplikace. Nastavení rozsahu aplikace lze změnit pouze při vytváření aplikace (prostřednictvím **Návrháře projektu**) nebo úpravou konfiguračního souboru aplikace. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Tento příklad používá <xref:System.Windows.Forms.PropertyGrid> ovládací prvek pro přístup k vlastnostem uživatelského nastavení `My.Settings` objektu. Ve výchozím nastavení <xref:System.Windows.Forms.PropertyGrid> zobrazuje všechny vlastnosti `My.Settings` objektu. Vlastnosti uživatelského nastavení ale mají <xref:System.Configuration.UserScopedSettingAttribute> atribut. Tento příklad nastaví <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> vlastnost na hodnotu <xref:System.Windows.Forms.PropertyGrid> , <xref:System.Configuration.UserScopedSettingAttribute> aby zobrazovala pouze vlastnosti uživatelského nastavení.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Přidání mřížky vlastností uživatelského nastavení  
  
1. Přidejte ovládací prvek **PropertyGrid** ze **sady nástrojů** na návrhovou plochu pro vaši aplikaci, která je `Form1`považována za.  
  
     Výchozím názvem ovládacího prvku mřížky vlastností je `PropertyGrid1`.  
  
2. Dvojitým kliknutím na návrhovou plochu `Form1` pro otevřete kód pro obslužnou rutinu události načtení formuláře.  
  
3. Nastavte `My.Settings` objekt jako vybraný objekt pro mřížku vlastností.  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. Nakonfigurujte mřížku vlastností tak, aby zobrazovala pouze uživatelská nastavení.  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > Chcete-li zobrazit pouze nastavení rozsahu aplikace, použijte <xref:System.Configuration.ApplicationScopedSettingAttribute> atribut namísto. <xref:System.Configuration.UserScopedSettingAttribute>  
  
## <a name="robust-programming"></a>Robustní programování  

 Aplikace uloží nastavení uživatele, když se aplikace vypíná. Chcete-li nastavení uložit hned, zavolejte `My.Settings.Save` metodu. Další informace najdete v tématu [Postup: zachování uživatelských nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Viz také

- [Objekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Postupy: Čtení nastavení aplikace v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Postupy: Změna uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Postupy: Zachování uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
