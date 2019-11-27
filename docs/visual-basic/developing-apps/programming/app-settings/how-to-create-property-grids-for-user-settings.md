---
title: 'Postupy: vytváření mřížek vlastností pro uživatelská nastavení'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: bed4e8a2b50f0115c3b8d9d6abf427df5f216388
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329615"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic

Mřížku vlastností pro uživatelské nastavení můžete vytvořit naplněním ovládacího prvku <xref:System.Windows.Forms.PropertyGrid> pomocí vlastností uživatelského nastavení objektu `My.Settings`.  
  
> [!NOTE]
> Aby tento příklad fungoval, musí mít vaše aplikace nastavené uživatelské nastavení. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Objekt `My.Settings` zpřístupňuje každé nastavení jako vlastnost. Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení. **Rozsah** nastavení určuje, zda je vlastnost určena pouze pro čtení; vlastnost pro nastavení rozsahu **aplikace**je jen pro čtení a vlastnost pro nastavení rozsahu **uživatele**je pro čtení i zápis. Další informace najdete v tématu [objekt My. Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> V době běhu nemůžete změnit ani uložit hodnoty nastavení rozsahu aplikace. Nastavení rozsahu aplikace lze změnit pouze při vytváření aplikace (prostřednictvím **Návrháře projektu**) nebo úpravou konfiguračního souboru aplikace. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Tento příklad používá ovládací prvek <xref:System.Windows.Forms.PropertyGrid> pro přístup k vlastnostem uživatelského nastavení objektu `My.Settings`. Ve výchozím nastavení <xref:System.Windows.Forms.PropertyGrid> zobrazuje všechny vlastnosti objektu `My.Settings`. Vlastnosti uživatelského nastavení ale mají atribut <xref:System.Configuration.UserScopedSettingAttribute>. V tomto příkladu se nastaví vlastnost <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> <xref:System.Windows.Forms.PropertyGrid> na <xref:System.Configuration.UserScopedSettingAttribute>, aby se zobrazily pouze vlastnosti uživatelského nastavení.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Přidání mřížky vlastností uživatelského nastavení  
  
1. Přidejte ovládací prvek **PropertyGrid** ze **sady nástrojů** na návrhovou plochu pro vaši aplikaci, která se předpokládá `Form1`.  
  
     Výchozí název ovládacího prvku mřížky vlastnosti je `PropertyGrid1`.  
  
2. Dvojím kliknutím na návrhovou plochu pro `Form1` otevřete kód pro obslužnou rutinu události načtení formuláře.  
  
3. Nastavte objekt `My.Settings` jako vybraný objekt pro mřížku vlastností.  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. Nakonfigurujte mřížku vlastností tak, aby zobrazovala pouze uživatelská nastavení.  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > Chcete-li zobrazit pouze nastavení rozsahu aplikace, použijte atribut <xref:System.Configuration.ApplicationScopedSettingAttribute> místo <xref:System.Configuration.UserScopedSettingAttribute>.  
  
## <a name="robust-programming"></a>Robustní programování  

 Aplikace uloží nastavení uživatele, když se aplikace vypíná. Chcete-li nastavení uložit hned, zavolejte metodu `My.Settings.Save`. Další informace najdete v tématu [Postup: zachování uživatelských nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Viz také:

- [Objekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Postupy: čtení nastavení aplikace v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Postupy: Změna uživatelského nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Postupy: zachování uživatelských nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
