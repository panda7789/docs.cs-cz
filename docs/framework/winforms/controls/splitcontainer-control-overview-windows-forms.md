---
title: SplitContainer – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 81898e09ff513043b205cde13378ae24ee755226
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45679580"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.SplitContainer> ovládací prvek lze považovat za složeného; je dva panely oddělené přesouvatelný panelu. Když je ukazatel myši nad panelu, ukazatel se změní tvar, který má zobrazit, že panel je přesouvatelný.  
  
> [!IMPORTANT]
>  V **nástrojů**, <xref:System.Windows.Forms.SplitContainer> řídit nahradí <xref:System.Windows.Forms.Splitter> ovládací prvek, který byl existuje v předchozí verzi sady Visual Studio. <xref:System.Windows.Forms.SplitContainer> Je mnohem upřednostňované nad ovládací prvek <xref:System.Windows.Forms.Splitter> ovládacího prvku. <xref:System.Windows.Forms.Splitter> Třídy je stále součástí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] z důvodu kompatibility se stávajícími aplikacemi, ale důrazně doporučujeme použít <xref:System.Windows.Forms.SplitContainer> ovládací prvek pro nové projekty.  
  
 S <xref:System.Windows.Forms.SplitContainer> ovládacího prvku, můžete vytvořit komplexní uživatelská rozhraní; často, výběr v jeden panel Určuje, jaké objekty jsou uvedeny na panelu. Toto uspořádání se velice efektivní pro zobrazení informací o procházení. Dva panely umožňuje agregovat informace v oblastech s panelu, nebo "rozdělovač," usnadňuje uživatelům změnit velikost panelů.  
  
 Více než jeden <xref:System.Windows.Forms.SplitContainer> ovládací prvek lze také vnořit, s druhým <xref:System.Windows.Forms.SplitContainer> ovládací prvek orientovaný vodorovně, chcete-li vytvořit panely horní a dolní.  
  
 Mějte na paměti, která <xref:System.Windows.Forms.SplitContainer> ovládací prvek je přístupná z klávesnice ve výchozím nastavení; uživatelé stisknutím klávesy se šipkami přesunutí příčky, pokud je <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> je nastavena na `false`.  
  
 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> Vlastnost <xref:System.Windows.Forms.SplitContainer> ovládací prvek určuje směr příčky, nikoli samotného ovládacího prvku. Proto pokud tato vlastnost nastavena na <xref:System.Windows.Forms.Orientation.Vertical>, příčky spustí shora dolů, vytváření panely vlevo a vpravo.  
  
 Navíc mějte na paměti, která hodnota <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> vlastnost se liší v závislosti na hodnotu <xref:System.Windows.Forms.SplitContainer.Orientation%2A> vlastnost. Další informace najdete v tématu <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> vlastnost.  
  
 Můžete taky omezit velikost a přesun <xref:System.Windows.Forms.SplitContainer> ovládacího prvku. <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> Určuje vlastnost panelu zůstane stejné velikosti po <xref:System.Windows.Forms.SplitContainer> změně velikosti ovládacího prvku a <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> vlastnost určuje, zda je příčka přesouvatelný pomocí klávesnice nebo myši.  
  
> [!NOTE]
>  I v případě <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> je nastavena na `true`, příčky může stále přesunout prostřednictvím kódu programu, například pomocí <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> vlastnost.  
  
 A konečně, jednotlivé panely <xref:System.Windows.Forms.SplitContainer> ovládací prvek má vlastnosti k určení jeho jednotlivé velikosti.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Běžně používané vlastnosti, metody a události  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> Vlastnost|Určuje panelu zůstanou stejné velikosti po <xref:System.Windows.Forms.SplitContainer> změně velikosti ovládacího prvku.|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Vlastnost|Určuje, zda lze přesunout příčky pomocí klávesnice nebo myši.|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A> Vlastnost|Určuje, pokud je příčky uspořádat vodorovně nebo svisle.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> Vlastnost|Určuje vzdálenost v pixelech přesouvatelný příčky od levého nebo horního okraje.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Vlastnost|Určuje minimální vzdálenost v pixelech, může uživatel přesune příčky.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> Vlastnost|Určuje tloušťku v pixelech, od rozdělovače.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving> Události|Vyvolá se při přesunutí příčky.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved> Události|Nastane, pokud má přesunutí příčky.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.SplitContainer>  
 [Ovládací prvek SplitContainer](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [Ukázka ovládacího prvku SplitContainer](https://msdn.microsoft.com/library/9015fad0-7108-4d85-a83a-a72d038c4f65)
