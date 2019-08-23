---
title: SplitContainer – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 76299d9bbd2b3eac4e765dfacf579c9979721fff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963212"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer – přehled ovládacího prvku (Windows Forms)
Ovládací prvek <xref:System.Windows.Forms.SplitContainer> model Windows Forms lze představit jako složený; jedná se o dva panely oddělené pohyblivým pruhem. Když je ukazatel myši nad pruhem, ukazatel se změní na obrazec, který ukazuje, že je pruh přesunutý.  
  
> [!IMPORTANT]
> Ovládací prvek v <xref:System.Windows.Forms.Splitter> **sadě nástrojů** <xref:System.Windows.Forms.SplitContainer> nahradí ovládací prvek, který byl v předchozí verzi sady Visual Studio. Ovládací prvek je mnohem upřednostňovaný <xref:System.Windows.Forms.Splitter> nad ovládacím prvkem. <xref:System.Windows.Forms.SplitContainer> Třída je stále zahrnuta v .NET Framework z důvodu kompatibility s existujícími aplikacemi, ale důrazně doporučujeme <xref:System.Windows.Forms.SplitContainer> používat ovládací prvek pro nové projekty. <xref:System.Windows.Forms.Splitter>  
  
 <xref:System.Windows.Forms.SplitContainer> Pomocí ovládacího prvku můžete vytvářet složitá uživatelská rozhraní, často výběr na jednom panelu určuje, které objekty se zobrazí na druhém panelu. Toto uspořádání je velmi efektivní pro zobrazení a informace o procházení. Když máte dva panely, můžete agregovat informace v oblastech a pruh nebo "rozdělovač", aby uživatelé mohli snadno měnit velikost panelů.  
  
 Více než jeden <xref:System.Windows.Forms.SplitContainer> ovládací prvek může být vnořen také s druhým <xref:System.Windows.Forms.SplitContainer> ovládacím prvkem orientovaným vodorovně, aby bylo možné vytvořit horní a dolní panel.  
  
 Mějte na <xref:System.Windows.Forms.SplitContainer> paměti, že ve výchozím nastavení je ovládací prvek přístupný pro přístup k klávesnicím. <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Pokud je vlastnost nastavena na `false`hodnotu, mohou uživatelé pomocí kláves se šipkami přesunout rozdělovač.  
  
 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> Vlastnost<xref:System.Windows.Forms.SplitContainer> ovládacího prvku určuje směr rozdělovače, nikoli samotného ovládacího prvku. Proto pokud je tato vlastnost nastavena na <xref:System.Windows.Forms.Orientation.Vertical>, je příčka spuštěna shora dolů a vytvoří levé a pravé panely.  
  
 Kromě toho mějte na paměti, že hodnota <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> vlastnosti se liší v závislosti na hodnotě <xref:System.Windows.Forms.SplitContainer.Orientation%2A> vlastnosti. Další informace najdete v tématu <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> vlastnost.  
  
 Můžete také omezit velikost a pohyb <xref:System.Windows.Forms.SplitContainer> ovládacího prvku. Vlastnost určuje, který panel zůstane <xref:System.Windows.Forms.SplitContainer> po <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> změně velikosti ovládacího prvku stejné velikosti a vlastnost určuje, zda je příčka přesunuta pomocí klávesnice nebo myši. <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>  
  
> [!NOTE]
> I v případě <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> , že je vlastnost `true`nastavena na, může být rozdělovač stále přesunut programově, <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> například pomocí vlastnosti.  
  
 Nakonec mají jednotlivé panely <xref:System.Windows.Forms.SplitContainer> ovládacího prvku vlastnosti pro určení jeho individuální velikosti.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Běžně používané vlastnosti, metody a události  
  
|Name|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>majetek|Určuje, která paleta zůstane po <xref:System.Windows.Forms.SplitContainer> změně velikosti ovládacího prvku stejná.|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>majetek|Určuje, zda lze příčku přesunout pomocí klávesnice nebo myši.|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A>majetek|Určuje, zda je příčka uspořádána svisle nebo vodorovně.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>majetek|Určuje vzdálenost v pixelech od levého nebo horního okraje až po Pohyblivý dělicí panel.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>majetek|Určuje minimální vzdálenost (v pixelech), po kterou může být příčka přesunuta uživatelem.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A>majetek|Určuje tloušťku příčky (v pixelech).|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving>událostí|Vyvolá se při přesunutí příčky.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved>událostí|Vyvolá se v případě, že došlo k přesunutí příčky.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.SplitContainer>
- [Ovládací prvek SplitContainer](splitcontainer-control-windows-forms.md)
- [Ukázka ovládacího prvku SplitContainer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/0ffz7d1b(v=vs.90))
