---
title: SplitContainer – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 9eea7d397824e443c46acff73fe6db0e43bcfe42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.SplitContainer> řízení lze považovat za složené; je dva panely oddělených mobilní panelu. Když ukazatel myši nad panelu, změní tvar, který má zobrazit, že je na panelu mobilní.  
  
> [!IMPORTANT]
>  V **sada nástrojů**, <xref:System.Windows.Forms.SplitContainer> řízení nahradí <xref:System.Windows.Forms.Splitter> ovládací prvek, který se někdo u předchozích verzí sady Visual Studio. <xref:System.Windows.Forms.SplitContainer> Ovládací prvek je mnohem upřednostňované přes <xref:System.Windows.Forms.Splitter> ovládacího prvku. <xref:System.Windows.Forms.Splitter> Třída je stále součástí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pro kompatibilitě se stávajícími aplikacemi, ale důrazně doporučujeme používat <xref:System.Windows.Forms.SplitContainer> ovládací prvek pro nové projekty.  
  
 Pomocí <xref:System.Windows.Forms.SplitContainer> ovládací prvek, můžete vytvořit komplexní uživatelská rozhraní; často výběr jeden panelu určuje, které objekty se zobrazují panelu. Toto uspořádání je velmi efektivní pro zobrazení a procházení informace. S dvěma panelů umožňuje agregovat informace v oblastech, a panelu nebo "rozdělovače," usnadňuje uživatelům změnit velikost panely.  
  
 Více než jeden <xref:System.Windows.Forms.SplitContainer> řízení mohou být také vnořené, s druhou <xref:System.Windows.Forms.SplitContainer> řízení orientován vodorovně, vytvořit horní a dolní panelů.  
  
 Mějte na paměti, <xref:System.Windows.Forms.SplitContainer> je přístupný z klávesnice ve výchozím nastavení řízení; uživatelé stisknutím klávesy se šipkami přesunout rozdělovače, pokud <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> je nastavena na `false`.  
  
 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> Vlastnost <xref:System.Windows.Forms.SplitContainer> řízení Určuje směr, rozdělovače, není z ovládacího prvku. Proto, pokud je tato vlastnost nastavená na <xref:System.Windows.Forms.Orientation.Vertical>, běží rozdělovače shora dolů, vytváření panelů vlevo a vpravo.  
  
 Kromě toho mějte na paměti, hodnota <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> vlastnost se liší v závislosti na hodnotě <xref:System.Windows.Forms.SplitContainer.Orientation%2A> vlastnost. Další informace najdete v tématu <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> vlastnost.  
  
 Můžete taky omezit velikost a pohybu <xref:System.Windows.Forms.SplitContainer> ovládacího prvku. <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> Vlastnost určuje, které panel zůstane stejnou velikost po <xref:System.Windows.Forms.SplitContainer> po změně velikosti a <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> vlastnost určuje, zda rozdělovače mobilní klávesnice nebo myš.  
  
> [!NOTE]
>  I když <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> je nastavena na `true`, rozdělovače může stále přesunout prostřednictvím kódu programu, například pomocí <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> vlastnost.  
  
 Nakonec, jednotlivé panely <xref:System.Windows.Forms.SplitContainer> řízení má vlastnosti k určení jeho jednotlivé velikosti.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Běžně používané vlastnosti, metod a události  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> Vlastnost|Určuje, které panel zůstane stejný velikost po <xref:System.Windows.Forms.SplitContainer> po změně velikosti.|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Vlastnost|Určuje, zda lze přesunout rozdělovače s klávesnici nebo myš.|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A> Vlastnost|Určuje, pokud je rozdělovače uspořádané vodorovně nebo svisle.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> Vlastnost|Určuje vzdálenost v pixelech od levého nebo horního okraje mobilní dělicí panel.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Vlastnost|Určuje minimální vzdálenost v pixelech, že rozdělovače lze přesunout uživatelem.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> Vlastnost|Určuje tloušťku v pixelech rozdělovače.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving> Události|Nastane, když je rozdělovače přesunutí.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved> Události|Nastane, když rozdělovače přesunul.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.SplitContainer>  
 [Ovládací prvek SplitContainer](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [Ukázka ovládacího prvku SplitContainer](http://msdn.microsoft.com/library/9015fad0-7108-4d85-a83a-a72d038c4f65)
