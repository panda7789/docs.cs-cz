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
ms.openlocfilehash: 32bcbab585c39be4a72150bf49820d4a16f1691f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968253"
---
# <a name="rendering-controls-with-visual-styles"></a>Vykreslování ovládacích prvků s vizuálními styly
.NET Framework poskytuje podporu pro vykreslování ovládacích prvků a dalších prvků uživatelského rozhraní systému Windows pomocí vizuálních stylů v operačních systémech, které je podporují. Toto téma popisuje několik úrovní podpory v .NET Framework pro vykreslování ovládacích prvků a dalších prvků uživatelského rozhraní s aktuálním vizuálním stylem operačního systému.  
  
## <a name="rendering-classes-for-common-controls"></a>Vykreslení tříd pro běžné ovládací prvky  
 Vykreslení ovládacího prvku odkazuje na vykreslování uživatelského rozhraní ovládacího prvku. <xref:System.Windows.Forms?displayProperty=nameWithType> Obor názvů <xref:System.Windows.Forms.ControlPaint> poskytuje třídu pro vykreslování některých běžných model Windows Formsch ovládacích prvků. Tato třída však vykresluje ovládací prvky v klasickém stylu Windows, což může ztížit zachování konzistentního uživatelského rozhraní při vykreslování vlastních ovládacích prvků v aplikacích s povolenými vizuálními styly.  
  
 .NET Framework 2,0 obsahuje třídy v <xref:System.Windows.Forms?displayProperty=nameWithType> oboru názvů, které vykreslují části a stavy běžných ovládacích prvků pomocí vizuálních stylů. Každá z těchto tříd obsahuje `static` metody pro vykreslení ovládacího prvku nebo částí ovládacího prvku v určitém stavu s aktuálním vizuálním stylem operačního systému.  
  
 Některé z těchto tříd jsou navrženy pro vykreslení souvisejícího ovládacího prvku bez ohledu na to, zda jsou vizuální styly k dispozici. Pokud jsou vizuální styly povoleny, pak členové třídy nakreslí související ovládací prvek s vizuálními styly; Pokud jsou vizuální styly zakázané, pak členové třídy nakreslí ovládací prvek na klasický styl oken. Mezi tyto třídy patří:  
  
- <xref:System.Windows.Forms.ButtonRenderer>  
  
- <xref:System.Windows.Forms.CheckBoxRenderer>  
  
- <xref:System.Windows.Forms.GroupBoxRenderer>  
  
- <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 Jiné třídy mohou nakreslit pouze související ovládací prvek, pokud jsou k dispozici vizuální styly a jejich členové budou generovat výjimku, pokud jsou vizuální styly zakázané. Mezi tyto třídy patří:  
  
- <xref:System.Windows.Forms.ComboBoxRenderer>  
  
- <xref:System.Windows.Forms.ProgressBarRenderer>  
  
- <xref:System.Windows.Forms.ScrollBarRenderer>  
  
- <xref:System.Windows.Forms.TabRenderer>  
  
- <xref:System.Windows.Forms.TextBoxRenderer>  
  
- <xref:System.Windows.Forms.TrackBarRenderer>  
  
 Další informace o použití těchto tříd k nakreslení ovládacího prvku naleznete v [tématu How to: Použijte třídu](how-to-use-a-control-rendering-class.md)vykreslování ovládacího prvku.  
  
## <a name="visual-style-element-and-rendering-classes"></a>Prvky vizuálního stylu a třídy vykreslování  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Obor názvů obsahuje třídy, které lze použít k vykreslení a získání informací o jakémkoli ovládacím prvku nebo prvku uživatelského rozhraní, které jsou podporovány vizuálními styly. Podporované ovládací prvky obsahují běžné ovládací prvky, které mají třídu vykreslování <xref:System.Windows.Forms?displayProperty=nameWithType> v oboru názvů (viz předchozí část), a také jiné ovládací prvky, například ovládací prvky karty a ovládací prvky matrice. Mezi další podporované prvky uživatelského rozhraní patří části nabídky **Start** , hlavní panel a neklientská oblast systému Windows.  
  
 Hlavní třídy <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> oboru názvů jsou <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> a <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>. <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>je základní třída pro identifikaci ovládacího prvku nebo prvku uživatelského rozhraní podporovaného vizuálními styly. Kromě <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> sebe sama <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> obor názvů <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> obsahuje mnoho vnořených tříd s `static` vlastnostmi, které vracejí <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> pro každý stav ovládacího prvku, části ovládacího prvku nebo jiného prvku uživatelského rozhraní podporovaného jazykem Visual Nadpis.  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>poskytuje metody, které nakreslí a získávají informace o <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> každém z nich definované aktuálním vizuálním stylem operačního systému. Informace, které mohou být načteny o elementu, obsahují výchozí velikost, typ pozadí a definice barev. <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>zabalí funkce rozhraní API pro vizuální styly (UxTheme) z prostředí Windows Platform SDK pro Windows. Další informace najdete v tématu [Povolení vizuálních stylů](/windows/desktop/controls/cookbook-overview).  
  
 Další informace o použití <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> a <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>naleznete v tématu [How to: Vykreslení elementu](how-to-render-a-visual-style-element.md)vizuálního stylu.  
  
## <a name="enabling-visual-styles"></a>Povolení vizuálních stylů  
 Chcete-li povolit vizuální styly pro aplikaci napsanou pro .NET Framework verze 1,0, programátoři musí zahrnovat manifest aplikace, který určuje, že ComCtl32. dll verze 6 nebo novější bude použit k vykreslení ovládacích prvků. Aplikace vytvořené pomocí .NET Framework verze 1,1 nebo novější mohou používat <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metodu <xref:System.Windows.Forms.Application> třídy.  
  
## <a name="checking-for-visual-styles-support"></a>Kontroluje se podpora vizuálních stylů.  
 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> Vlastnost<xref:System.Windows.Forms.Application> třídy označuje, zda je aktuální aplikace nakreslena ovládacími prvky pomocí vizuálních stylů. Při malování vlastního ovládacího prvku lze zjistit hodnotu <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> , chcete-li určit, zda je nutné vykreslit ovládací prvek s vizuálními styly nebo bez nich. V následující tabulce jsou uvedeny čtyři podmínky, které musí existovat <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> pro návrat `true`.  
  
|Podmínka|Poznámky|  
|---------------|-----------|  
|Operační systém podporuje vizuální styly.|Chcete-li ověřit tuto podmínku samostatně, <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> použijte vlastnost <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> třídy.|  
|Uživatel povolil v operačním systému vizuální styly.|Chcete-li ověřit tuto podmínku samostatně, <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> použijte vlastnost <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> třídy.|  
|V aplikaci jsou povoleny vizuální styly.|Vizuální styly lze povolit v aplikaci voláním <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody nebo pomocí manifestu aplikace, který určuje, že Comctl32. dll verze 6 nebo novější bude použit k vykreslení ovládacích prvků.|  
|Vizuální styly jsou používány k vykreslení klientské oblasti oken aplikace.|Chcete-li ověřit tuto podmínku samostatně, <xref:System.Windows.Forms.Application.VisualStyleState%2A> použijte vlastnost <xref:System.Windows.Forms.Application> třídy a ověřte, zda má hodnotu <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAreaEnabled?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAndNonClientAreasEnabled?displayProperty=nameWithType>.|  
  
 Chcete-li určit, kdy uživatel povoluje nebo zakazuje vizuální styly nebo přepne z jednoho vizuálního stylu do jiného <xref:Microsoft.Win32.UserPreferenceCategory.VisualStyle?displayProperty=nameWithType> , zkontrolujte hodnotu v obslužných <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=nameWithType> rutinách událostí nebo <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=nameWithType> .  
  
> [!IMPORTANT]
> Pokud chcete použít <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> k vykreslení ovládacího prvku nebo prvku uživatelského rozhraní, když uživatel povolí nebo přepne vizuální styly, ujistěte se, že to uděláte při <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> zpracování události namísto <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> události. Pokud použijete <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> třídu při zpracování <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging>, bude vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také:

- [Malování a vykreslování vlastního ovládacího prvku](custom-control-painting-and-rendering.md)
