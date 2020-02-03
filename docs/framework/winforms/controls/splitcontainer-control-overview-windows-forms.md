---
title: Přehled ovládacího prvku SplitContainer
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 5cb5240ed4ebe3e27c20844681068711c222e9a9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742919"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer – přehled ovládacího prvku (Windows Forms)
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.SplitContainer> lze představit jako složený; Jedná se o dva panely oddělené pohyblivým pruhem. Když je ukazatel myši nad pruhem, ukazatel se změní na obrazec, který ukazuje, že je pruh přesunutý.  
  
> [!IMPORTANT]
> V **sadě nástrojů**<xref:System.Windows.Forms.SplitContainer> ovládací prvek nahrazuje ovládací prvek <xref:System.Windows.Forms.Splitter>, který byl v předchozí verzi sady Visual Studio. Ovládací prvek <xref:System.Windows.Forms.SplitContainer> je pro <xref:System.Windows.Forms.Splitter> řízení mnohem upřednostňovaný. Třída <xref:System.Windows.Forms.Splitter> je stále zahrnuta v .NET Framework kvůli kompatibilitě se stávajícími aplikacemi, ale důrazně doporučujeme používat ovládací prvek <xref:System.Windows.Forms.SplitContainer> pro nové projekty.  
  
 Pomocí ovládacího prvku <xref:System.Windows.Forms.SplitContainer> můžete vytvářet složitá uživatelská rozhraní; často výběr na jednom panelu určuje, které objekty se zobrazí na druhém panelu. Toto uspořádání je velmi efektivní pro zobrazení a informace o procházení. Když máte dva panely, můžete agregovat informace v oblastech a pruh nebo "rozdělovač", aby uživatelé mohli snadno měnit velikost panelů.  
  
 Více než jeden ovládací prvek <xref:System.Windows.Forms.SplitContainer> může být vnořen i druhý ovládací prvek <xref:System.Windows.Forms.SplitContainer> orientovaný vodorovně, aby bylo možné vytvořit horní a dolní panel.  
  
 Mějte na paměti, že ve výchozím nastavení je ovládací prvek <xref:System.Windows.Forms.SplitContainer> přístupný z klávesnice. Uživatelé mohou stisknutím kláves se šipkami přesunout rozdělovač, pokud je vlastnost <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> nastavena na hodnotu `false`.  
  
 Vlastnost <xref:System.Windows.Forms.SplitContainer.Orientation%2A> ovládacího prvku <xref:System.Windows.Forms.SplitContainer> určuje směr rozdělovače, nikoli samotného ovládacího prvku. Proto pokud je tato vlastnost nastavená na <xref:System.Windows.Forms.Orientation.Vertical>, rozdělovač se spustí shora dolů a vytvoří levé a pravé panely.  
  
 Kromě toho mějte na paměti, že hodnota vlastnosti <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> se liší v závislosti na hodnotě vlastnosti <xref:System.Windows.Forms.SplitContainer.Orientation%2A>. Další informace najdete v tématu <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> vlastnosti.  
  
 Můžete také omezit velikost a pohyb ovládacího prvku <xref:System.Windows.Forms.SplitContainer>. Vlastnost <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> určuje, který panel zůstane stejný velikost po změně velikosti ovládacího prvku <xref:System.Windows.Forms.SplitContainer> a vlastnost <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> určuje, zda je příčka přesunuta pomocí klávesnice nebo myši.  
  
> [!NOTE]
> I v případě, že je vlastnost <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> nastavena na hodnotu `true`, rozdělovač může být stále přesunut programově; například pomocí vlastnosti <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>.  
  
 Nakonec každý panel ovládacího prvku <xref:System.Windows.Forms.SplitContainer> má vlastnosti pro určení jeho individuální velikosti.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Běžně používané vlastnosti, metody a události  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> – vlastnost|Určuje, která paleta zůstane po změně velikosti <xref:System.Windows.Forms.SplitContainer> ovládacího prvku stejná velikost.|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> – vlastnost|Určuje, zda lze příčku přesunout pomocí klávesnice nebo myši.|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A> – vlastnost|Určuje, zda je příčka uspořádána svisle nebo vodorovně.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> – vlastnost|Určuje vzdálenost v pixelech od levého nebo horního okraje až po Pohyblivý dělicí panel.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> – vlastnost|Určuje minimální vzdálenost (v pixelech), po kterou může být příčka přesunuta uživatelem.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> – vlastnost|Určuje tloušťku příčky (v pixelech).|  
|událost <xref:System.Windows.Forms.SplitContainer.SplitterMoving>|Vyvolá se při přesunutí příčky.|  
|událost <xref:System.Windows.Forms.SplitContainer.SplitterMoved>|Vyvolá se v případě, že došlo k přesunutí příčky.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.SplitContainer>
- [Ovládací prvek SplitContainer](splitcontainer-control-windows-forms.md)
- [Ukázka ovládacího prvku SplitContainer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/0ffz7d1b(v=vs.90))
