---
title: "Vykreslování ovládacích prvků s vizuálními styly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- themes [Windows Forms], XP visual styles in Window Forms
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- visual themes [Windows Forms], rendering Windows Forms controls
- user controls [Windows Forms], painting
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a5b178ba-610e-46c4-a6c0-509c0886a744
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 127e3c411b4c75e5a2bd9f133defc447992b95f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="rendering-controls-with-visual-styles"></a>Vykreslování ovládacích prvků s vizuálními styly
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Poskytuje podporu pro vykreslení ovládacích prvků a ostatní uživatele systému Windows prvky rozhraní (UI) pomocí vizuální styly v operačních systémech, které je podporují. Toto téma popisuje několik úrovní podporu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pro vykreslování a další prvky uživatelského rozhraní s aktuální vizuální styl operačního systému.  
  
## <a name="rendering-classes-for-common-controls"></a>Třídy vykreslování pro běžné ovládací prvky  
 Vykreslení ovládacího prvku, odkazuje na kreslení uživatelské rozhraní ovládacího prvku. <xref:System.Windows.Forms?displayProperty=nameWithType> Obor názvů obsahuje <xref:System.Windows.Forms.ControlPaint> třídy pro vykreslování některé běžné ovládací prvky Windows Forms. Tato třída však nevykresluje ovládací prvky v klasický styl systému Windows, který může být obtížné zachovat konzistentního prostředí uživatelského rozhraní při kreslení vlastní ovládací prvky v aplikacích s vizuálními styly povolena.  
  
 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] Zahrnuje třídy v <xref:System.Windows.Forms?displayProperty=nameWithType> obor názvů, který vykreslení částí a stavy společných ovládacích prvků s vizuálními styly. Každá z těchto tříd zahrnuje `static` metody pro vykreslení ovládacího prvku nebo částí ovládacího prvku v určitém stavu s aktuální vizuální styl operačního systému.  
  
 Některé z těchto tříd slouží k vykreslení ovládacího prvku související bez ohledu na to, jestli jsou k dispozici vizuální styly. Pokud jsou povolené vizuální styly, pak členy třídy bude kreslení související ovládací prvek s vizuálními styly; Pokud jsou zakázány vizuální styly, pak členy třídy bude zakreslit ovládacího prvku ve klasický styl systému Windows. Tyto třídy patří:  
  
-   <xref:System.Windows.Forms.ButtonRenderer>  
  
-   <xref:System.Windows.Forms.CheckBoxRenderer>  
  
-   <xref:System.Windows.Forms.GroupBoxRenderer>  
  
-   <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 Ostatní třídy pouze když vizuální styly jsou k dispozici, a jejich členové vyvolá výjimku, pokud jsou zakázány vizuální styly nakreslit související ovládací prvek. Tyto třídy patří:  
  
-   <xref:System.Windows.Forms.ComboBoxRenderer>  
  
-   <xref:System.Windows.Forms.ProgressBarRenderer>  
  
-   <xref:System.Windows.Forms.ScrollBarRenderer>  
  
-   <xref:System.Windows.Forms.TabRenderer>  
  
-   <xref:System.Windows.Forms.TextBoxRenderer>  
  
-   <xref:System.Windows.Forms.TrackBarRenderer>  
  
 Další informace o použití těchto tříd k vykreslení ovládacího prvku, najdete v části [postupy: použití třídy vykreslování ovládacího prvku](../../../../docs/framework/winforms/controls/how-to-use-a-control-rendering-class.md).  
  
## <a name="visual-style-element-and-rendering-classes"></a>Elementu vizuálního stylu a vykreslování třídy  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Obor názvů obsahuje třídy, které lze použít k vykreslení a získat informace o všech element uživatelského rozhraní, který podporuje vizuální styly nebo ovládací prvek. Podporované ovládací prvky zahrnují běžné ovládací prvky, které mají třídu vykreslování v <xref:System.Windows.Forms?displayProperty=nameWithType> obor názvů (viz předchozí části), a také další ovládací prvky, jako jsou ovládací prvky karet a ovládací prvky matrice. Zahrnout další podporované elementy uživatelského rozhraní části **spustit** nabídky, na hlavním panelu a oblasti nonclient systému windows.  
  
 Hlavní třídy <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> obor názvů jsou <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> a <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>. <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>je třída foundation pro identifikaci libovolného uživatele nebo ovládací prvek elementu rozhraní, nepodporuje vizuální styly. Kromě <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> samostatně, <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> obor názvů zahrnuje mnoho vnořené třídy <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> s `static` vlastnosti, které vracejí <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> pro každý stav ovládacího prvku, část řízení nebo jiného uživatelského rozhraní elementu nepodporuje visual styly.  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>poskytuje metody, které kreslení a získat informace o jednotlivých <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> definované aktuální vizuální styl operačního systému. Informace o elementu, které se dá načíst zahrnuje jeho výchozí velikost, typ pozadí a barvu definice. <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>zabalí funkci vizuální styly (UxTheme) rozhraní API z prostředí systému Windows část sady Windows SDK pro platformu. Další informace najdete v tématu [pomocí vizuální styly XP Windows](https://msdn.microsoft.com/library/ms997649.aspx).  
  
 Další informace o používání <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> a <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>, najdete v části [postupy: vykreslení Visual Style Element](../../../../docs/framework/winforms/controls/how-to-render-a-visual-style-element.md).  
  
## <a name="enabling-visual-styles"></a>Povolení vizuální styly  
 Chcete-li povolit pro aplikace napsané pro vizuální styly [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0, programátory musí obsahovat manifest aplikace, která určuje, že ComCtl32.dll verze 6 nebo novější, se použije k vykreslení ovládacích prvků. Aplikace sestavené s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1 nebo novější můžete použít <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metodu <xref:System.Windows.Forms.Application> třídy.  
  
## <a name="checking-for-visual-styles-support"></a>Kontrola podpora vizuální styly  
 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> Vlastnost <xref:System.Windows.Forms.Application> třída označuje, zda je aktuální aplikace vykreslování ovládacích prvků s vizuálními styly. Při vykreslování vlastního ovládacího prvku, můžete zkontrolovat hodnotu <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> k určení, zda mají vykreslovat ovládací prvek s nebo bez vizuální styly. Následující tabulka uvádí čtyři podmínky, které musí existovat <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> vrátit `true`.  
  
|Podmínka|Poznámky|  
|---------------|-----------|  
|Operační systém podporuje vizuální styly.|Chcete-li tuto podmínku ověřit odděleně, použijte <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> vlastnost <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> třídy.|  
|Uživatel aktivoval vizuální styly v operačním systému.|Chcete-li tuto podmínku ověřit odděleně, použijte <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> vlastnost <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> třídy.|  
|Vizuální styly jsou povolené v aplikaci.|Vizuální styly lze povolit v aplikaci při volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metoda nebo v aplikaci manifestu, který určuje, že verze souboru ComCtl32.dll 6 nebo novější se použije k vykreslení ovládacích prvků.|  
|Vizuální styly se používá k vykreslení klientské oblasti aplikace systému windows.|Chcete-li tuto podmínku ověřit odděleně, použijte <xref:System.Windows.Forms.Application.VisualStyleState%2A> vlastnost <xref:System.Windows.Forms.Application> třídy a ověřit, zda má hodnota <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAreaEnabled?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAndNonClientAreasEnabled?displayProperty=nameWithType>.|  
  
 Chcete-li zjistit, když uživatel povolí nebo zakáže vizuální styly nebo přepíná z jednoho vizuální styl na jiný, zkontrolujte <xref:Microsoft.Win32.UserPreferenceCategory.VisualStyle?displayProperty=nameWithType> hodnotu v obslužné rutiny <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=nameWithType> nebo <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=nameWithType> události.  
  
> [!IMPORTANT]
>  Pokud chcete použít <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> k vykreslení ovládacího prvku nebo elementu uživatelského rozhraní, když uživatel povolí nebo přepíná vizuální styly, ujistěte se, abyste to provedli při zpracování <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> událostí místo <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> událostí. Bude vyvolána výjimka, pokud použijete <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> třídy při zpracování <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging>.  
  
## <a name="see-also"></a>Viz také  
 [Malování a vykreslování vlastního ovládacího prvku](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)
