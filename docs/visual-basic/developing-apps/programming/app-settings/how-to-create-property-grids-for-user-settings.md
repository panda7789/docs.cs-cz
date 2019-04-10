---
title: 'Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: 5f4b962762aeecea65748c5456bc4a2d75595d4f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311614"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic
Můžete vytvořit mřížku vlastností pro uživatelská nastavení naplněním <xref:System.Windows.Forms.PropertyGrid> ovládacího prvku pomocí vlastnosti nastavení uživatele `My.Settings` objektu.  
  
> [!NOTE]
>  Aby tento příklad fungoval musí mít vaše aplikace nastavené uživatelské nastavení. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 `My.Settings` Objekt poskytuje každému nastavení jako vlastnost. Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typů nastavení. Toto nastavení **oboru** Určuje, zda je vlastnost jen pro čtení; vlastnost pro **aplikace**– obor nastavení je jen pro čtení, při vlastnost pro **uživatele**– oboru nastavení je pro čtení i zápis. Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Nelze změnit ani uložit hodnoty nastavení oboru aplikace v době běhu. Nastavení oboru aplikace lze změnit pouze při vytváření aplikace (prostřednictvím **Návrháře projektu**) nebo úpravou konfiguračního souboru aplikace. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Tento příklad používá <xref:System.Windows.Forms.PropertyGrid> ovládací prvek pro přístup k vlastnostem nastavení uživatele `My.Settings` objektu. Ve výchozím nastavení <xref:System.Windows.Forms.PropertyGrid> zobrazuje všechny vlastnosti `My.Settings` objektu. Ale mít vlastnosti uživatelského nastavení <xref:System.Configuration.UserScopedSettingAttribute> atribut. Tento příklad nastaví <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> vlastnost <xref:System.Windows.Forms.PropertyGrid> k <xref:System.Configuration.UserScopedSettingAttribute> zobrazit pouze vlastnosti nastavení uživatele.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Chcete-li přidat mřížky vlastností uživatelské nastavení  
  
1. Přidat **PropertyGrid** ovládacího prvku **nástrojů** na návrhovou plochu pro vaši aplikaci, předpokládá, že tady být `Form1`.  
  
     Výchozí název ovládacího prvku mřížky vlastností je `PropertyGrid1`.  
  
2. Klikněte dvakrát na návrhové ploše pro `Form1` otevřete kód pro obslužnou rutinu události nahrání formuláře.  
  
3. Nastavte `My.Settings` objektu jako vybraného objektu mřížky vlastností.  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. Nakonfigurujte mřížkou zobrazí pouze nastavení uživatele.  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    >  Chcete-li zobrazit pouze nastavení oboru aplikace, použijte <xref:System.Configuration.ApplicationScopedSettingAttribute> atribut namísto <xref:System.Configuration.UserScopedSettingAttribute>.  
  
## <a name="robust-programming"></a>Robustní programování  
 Aplikace ukládá uživatelská nastavení při ukončení aplikace. Chcete-li uložit nastavení okamžitě, zavolejte `My.Settings.Save` metody. Další informace najdete v tématu [jak: Zachování uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Viz také:

- [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Postupy: Čtení nastavení aplikace v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Postupy: Změna uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Postupy: Zachování uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
