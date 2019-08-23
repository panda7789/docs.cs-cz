---
title: 'Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: 4a31b44cca61caea5fdf725405646f628b5430b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968397"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v Visual Basic
Mřížku vlastností pro uživatelské nastavení můžete vytvořit naplněním <xref:System.Windows.Forms.PropertyGrid> ovládacího prvku pomocí vlastností `My.Settings` uživatelského nastavení objektu.  
  
> [!NOTE]
> Aby tento příklad fungoval, musí mít vaše aplikace nastavené uživatelské nastavení. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 `My.Settings` Objekt zpřístupňuje každé nastavení jako vlastnost. Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení. **Rozsah** nastavení určuje, zda je vlastnost určena pouze pro čtení; vlastnost pro nastavení rozsahu **aplikace**je jen pro čtení a vlastnost pro nastavení rozsahu **uživatele**je pro čtení i zápis. Další informace najdete v tématu [objekt My. Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> V době běhu nemůžete změnit ani uložit hodnoty nastavení rozsahu aplikace. Nastavení rozsahu aplikace lze změnit pouze při vytváření aplikace (prostřednictvím **Návrháře projektu**) nebo úpravou konfiguračního souboru aplikace. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Tento příklad používá <xref:System.Windows.Forms.PropertyGrid> ovládací prvek pro přístup k vlastnostem `My.Settings` uživatelského nastavení objektu. Ve výchozím nastavení <xref:System.Windows.Forms.PropertyGrid> zobrazuje všechny vlastnosti `My.Settings` objektu. Vlastnosti uživatelského nastavení ale mají <xref:System.Configuration.UserScopedSettingAttribute> atribut. Tento příklad nastaví <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> vlastnost na hodnotu <xref:System.Windows.Forms.PropertyGrid> <xref:System.Configuration.UserScopedSettingAttribute> , aby zobrazovala pouze vlastnosti uživatelského nastavení.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Přidání mřížky vlastností uživatelského nastavení  
  
1. Přidejte ovládací prvek **PropertyGrid** ze **sady nástrojů** na návrhovou plochu pro vaši aplikaci, která je `Form1`považována za.  
  
     Výchozím názvem ovládacího prvku mřížky vlastností je `PropertyGrid1`.  
  
2. Dvojitým kliknutím na návrhovou plochu `Form1` pro otevřete kód pro obslužnou rutinu události načtení formuláře.  
  
3. `My.Settings` Nastavte objekt jako vybraný objekt pro mřížku vlastností.  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. Nakonfigurujte mřížku vlastností tak, aby zobrazovala pouze uživatelská nastavení.  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > Chcete-li zobrazit pouze nastavení rozsahu aplikace, použijte <xref:System.Configuration.ApplicationScopedSettingAttribute> atribut <xref:System.Configuration.UserScopedSettingAttribute>namísto.  
  
## <a name="robust-programming"></a>Robustní programování  
 Aplikace uloží nastavení uživatele, když se aplikace vypíná. Chcete-li nastavení uložit hned, zavolejte `My.Settings.Save` metodu. Další informace najdete v tématu [jak: Zachovat uživatelská nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Viz také:

- [Objekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Postupy: Číst nastavení aplikace v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Postupy: Změna uživatelského nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Postupy: Zachovat uživatelská nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
