---
title: Vykreslování ovládacích prvků s vizuálními styly
ms.date: 03/30/2017
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- themes [Windows Forms], XP visual styles in Window Forms
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- visual themes [Windows Forms], rendering Windows Forms controls
- user controls [Windows Forms], painting
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a5b178ba-610e-46c4-a6c0-509c0886a744
ms.openlocfilehash: b0b301bca33842dfb68de9143b665bed73f17b74
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146767"
---
# <a name="rendering-controls-with-visual-styles"></a>Vykreslování ovládacích prvků s vizuálními styly
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Poskytuje podporu pro vykreslení ovládacích prvků a jiných uživatelů Windows pomocí vizuálních stylů v operačních systémech, které je podporují prvky rozhraní (UI). Toto téma popisuje několik úrovní podpory v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pro vykreslování a další prvky uživatelského rozhraní s aktuálním vizuálním stylem operačního systému.  
  
## <a name="rendering-classes-for-common-controls"></a>Třídy vykreslování pro běžné ovládací prvky  
 Vykreslení ovládacího prvku se vztahuje k vykreslení ovládacího prvku uživatelského rozhraní. <xref:System.Windows.Forms?displayProperty=nameWithType> Obor názvů poskytuje <xref:System.Windows.Forms.ControlPaint> ovládací prvky Windows Forms třídy pro vykreslování některé běžné. Tato třída však kreslení ovládacích prvků v klasického stylu Windows, který může být obtížné udržovat konzistentní prostředí uživatelského rozhraní při kreslení vlastních ovládacích prvků v aplikacích s vizuálními styly povoleny.  
  
 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] Zahrnuje třídy v <xref:System.Windows.Forms?displayProperty=nameWithType> obor názvů, který vykreslování části a stavy běžných ovládacích prvků s vizuálními styly. Každá z těchto tříd obsahuje `static` metody pro vykreslení ovládacího prvku nebo části ovládacího prvku v určitém stavu s aktuálním vizuálním stylem operačního systému.  
  
 Některé z těchto tříd jsou navržené k vykreslení související ovládací prvek bez ohledu na to, zda jsou k dispozici vizuální styly. Pokud jsou povolené vizuální styly, pak členy třídy bude nakreslete související s vizuálními styly; Pokud je vizuální styly jsou zakázané, pak členy třídy bude nakreslete ovládací prvek v klasické Windows. Tyto třídy zahrnují:  
  
-   <xref:System.Windows.Forms.ButtonRenderer>  
  
-   <xref:System.Windows.Forms.CheckBoxRenderer>  
  
-   <xref:System.Windows.Forms.GroupBoxRenderer>  
  
-   <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 Jiné třídy lze vykreslit související ovládací prvek při vizuální styly jsou k dispozici, a jejich členy vyvolá výjimku, pokud vizuální styly jsou zakázané. Tyto třídy zahrnují:  
  
-   <xref:System.Windows.Forms.ComboBoxRenderer>  
  
-   <xref:System.Windows.Forms.ProgressBarRenderer>  
  
-   <xref:System.Windows.Forms.ScrollBarRenderer>  
  
-   <xref:System.Windows.Forms.TabRenderer>  
  
-   <xref:System.Windows.Forms.TextBoxRenderer>  
  
-   <xref:System.Windows.Forms.TrackBarRenderer>  
  
 Další informace o použití těchto tříd k vykreslení ovládacího prvku, naleznete v tématu [jak: Použití třídy vykreslující ovládací prvek](how-to-use-a-control-rendering-class.md).  
  
## <a name="visual-style-element-and-rendering-classes"></a>Elementu vizuálního stylu a vykreslování třídy  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Obor názvů obsahuje třídy, které slouží k vykreslení a získat informace o jakýchkoli ovládacího prvku nebo prvku uživatelského rozhraní, který podporuje vizuální styly. Podporované ovládací prvky zahrnují běžné ovládací prvky, které mají třídy vykreslování <xref:System.Windows.Forms?displayProperty=nameWithType> obor názvů (viz předchozí oddíl), a také další ovládací prvky, jako je například ovládací prvky karet a ovládacích prvcích matrice. Další podporované prvky uživatelského rozhraní zahrnout části **Start** nabídky, na hlavním panelu a neklientské oblasti okna.  
  
 Hlavní třídy <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> obor názvů jsou <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> a <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>. <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> je třída foundation pro identifikaci libovolný prvek rozhraní ovládacího prvku nebo uživateli vizuální styly podporovány. Kromě <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> samostatně, <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> obor názvů obsahuje mnoho vnořené třídy typu <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> s `static` vlastnosti, které vracejí <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> pro každý stav ovládacího prvku, část ovládacího prvku nebo jiný prvek uživatelského rozhraní nepodporuje visual styly.  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> poskytuje metody, které nakreslíte a získat informace o jednotlivých <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> definována aktuálním vizuálním stylem operačního systému. Informace o elementu, které je možné načíst zahrnuje jeho výchozí velikost, typ pozadí a barvy definice. <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> zabalí funkci vizuálních stylů (UxTheme) rozhraní API z prostředí Windows část sady Windows SDK platformy. Další informace najdete v tématu [povolení vizuálních stylů](/windows/desktop/controls/cookbook-overview).  
  
 Další informace o používání <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> a <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>, naleznete v tématu [jak: Vykreslení elementu vizuálního stylu](how-to-render-a-visual-style-element.md).  
  
## <a name="enabling-visual-styles"></a>Povolení vizuálních stylů  
 K povolení vizuálních stylů pro aplikace napsané pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0, programátoři musí obsahovat manifest aplikace, která určuje, že knihovna ComCtl32.dll ve verzi 6 nebo novější se použije k vykreslení ovládacích prvků. Aplikace vytvořené pomocí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1 nebo novější můžete použít <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metodu <xref:System.Windows.Forms.Application> třídy.  
  
## <a name="checking-for-visual-styles-support"></a>Kontrolují se podpora vizuálních stylů  
 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> Vlastnost <xref:System.Windows.Forms.Application> třídy označuje, zda je aktuální aplikace nakreslením ovládacích prvků s vizuálními styly. Při vykreslování vlastního ovládacího prvku, můžete zkontrolovat hodnotu <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> k určení, zda by měl vykreslení ovládacího prvku s nebo bez něj vizuální styly. V následující tabulce jsou uvedeny čtyři podmínky, které nastává v případě <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> vrátit `true`.  
  
|Podmínka|Poznámky|  
|---------------|-----------|  
|Operační systém podporoval vizuální styly.|Chcete-li tuto podmínku ověřit samostatně, použijte <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> vlastnost <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> třídy.|  
|Uživatel aktivoval vizuálních stylů v operačním systému.|Chcete-li tuto podmínku ověřit samostatně, použijte <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> vlastnost <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> třídy.|  
|Vizuální styly jsou povoleny v aplikaci.|Vizuální styly lze povolit v aplikaci pomocí volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metoda nebo aplikaci manifestu, který určuje, že verze souboru ComCtl32.dll 6 nebo novější se použije k vykreslení ovládacích prvků.|  
|Vizuální styly jsou použity k vykreslení oblasti klienta aplikace pro windows|Chcete-li tuto podmínku ověřit samostatně, použijte <xref:System.Windows.Forms.Application.VisualStyleState%2A> vlastnost <xref:System.Windows.Forms.Application> třídy a ověřte, že má hodnotu <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAreaEnabled?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAndNonClientAreasEnabled?displayProperty=nameWithType>.|  
  
 Pokud chcete zjistit, když uživatele povolí nebo zakáže vizuální styly nebo z jednoho vizuálního stylu se přepne na jiný, zkontrolujte <xref:Microsoft.Win32.UserPreferenceCategory.VisualStyle?displayProperty=nameWithType> hodnotu v obslužných rutinách <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=nameWithType> nebo <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=nameWithType> události.  
  
> [!IMPORTANT]
>  Pokud chcete použít <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> k vykreslení ovládacího prvku nebo prvku uživatelského rozhraní, když uživatel povolí nebo přepne vizuální styly, ujistěte se, abyste to udělali při zpracování <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> události místo <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> událostí. Bude vyvolána výjimka, pokud použijete <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> třídy při zpracování <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging>.  
  
## <a name="see-also"></a>Viz také:

- [Malování a vykreslování vlastního ovládacího prvku](custom-control-painting-and-rendering.md)
