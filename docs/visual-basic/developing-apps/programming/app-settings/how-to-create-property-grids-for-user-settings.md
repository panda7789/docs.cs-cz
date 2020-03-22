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

Mřížku vlastností pro uživatelská nastavení můžete <xref:System.Windows.Forms.PropertyGrid> vytvořit vyplněním ovládacího `My.Settings` prvku vlastnostmi nastavení uživatele objektu.  
  
> [!NOTE]
> Aby tento příklad fungoval, musí mít aplikace nakonfigurovaná uživatelská nastavení. Další informace naleznete v [tématu Správa nastavení aplikací (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Objekt `My.Settings` zveřejňuje každé nastavení jako vlastnost. Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení. **Rozsah** nastavení určuje, zda je vlastnost jen pro čtení; vlastnost pro nastavení **Application**-scope je jen pro čtení, zatímco vlastnost pro nastavení **User**-scope je čtení a zápis. Další informace naleznete v tématu [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Hodnoty nastavení oboru aplikace nelze za běhu změnit ani uložit. Nastavení oboru aplikace lze změnit pouze při vytváření aplikace (prostřednictvím **Návrháře projektu)** nebo úpravou konfiguračního souboru aplikace. Další informace naleznete v [tématu Správa nastavení aplikací (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Tento příklad <xref:System.Windows.Forms.PropertyGrid> používá ovládací prvek pro přístup `My.Settings` k vlastnostem nastavení uživatele objektu. Ve výchozím <xref:System.Windows.Forms.PropertyGrid> nastavení zobrazuje všechny `My.Settings` vlastnosti objektu. Vlastnosti nastavení uživatele však <xref:System.Configuration.UserScopedSettingAttribute> mají atribut. Tento příklad <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> nastaví <xref:System.Windows.Forms.PropertyGrid> vlastnost <xref:System.Configuration.UserScopedSettingAttribute> to to zobrazit pouze vlastnosti nastavení uživatele.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Přidání mřížky vlastností nastavení uživatele  
  
1. Přidejte **propertygrid** ovládací prvek z **panelu nástrojů** na návrhovou `Form1`plochu pro vaši aplikaci, předpokládá se zde .  
  
     Výchozí název ovládacího prvku mřížky vlastností je `PropertyGrid1`.  
  
2. Poklepáním na návrhovou plochu otevřete `Form1` kód pro obslužnou rutinu události načtení formuláře.  
  
3. Nastavte `My.Settings` objekt jako vybraný objekt pro mřížku vlastností.  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. Nakonfigurujte mřížku vlastností tak, aby zobrazovala pouze uživatelská nastavení.  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > Chcete-li zobrazit pouze nastavení oboru <xref:System.Configuration.ApplicationScopedSettingAttribute> aplikace, <xref:System.Configuration.UserScopedSettingAttribute>použijte atribut namísto .  
  
## <a name="robust-programming"></a>Robustní programování  

 Aplikace uloží uživatelská nastavení při vypnutí aplikace. Chcete-li nastavení uložit `My.Settings.Save` okamžitě, zavolejte metodu. Další informace naleznete v [tématu How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Viz také

- [Objekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Postupy: Čtení nastavení aplikace v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Postupy: Změna uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Postupy: Zachování uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
