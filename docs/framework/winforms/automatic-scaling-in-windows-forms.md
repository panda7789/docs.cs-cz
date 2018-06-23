---
title: Automatická změna měřítka ve Windows Forms
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: 0018b9f8644ec7d222a416bb5f71a7c61671009e
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314760"
---
# <a name="automatic-scaling-in-windows-forms"></a>Automatická změna měřítka ve Windows Forms
Automatické škálování umožňuje formulář a jeho ovládacích prvků, navržená tak, na jeden počítač se určité zobrazení řešení nebo systém písmo, správně zobrazený na jiný počítač s jiným zobrazením řešení nebo systém písmo. Zaručuje, formulář a jeho ovládacích prvků bude inteligentně velikosti být v souladu s nativní windows a další aplikace na počítače uživatelů i ostatní vývojáři. Podporu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] pro automatické škálování a vizuální styly umožňuje [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] aplikace udržovat konzistentní vzhled a chování ve srovnání s nativní aplikace systému Windows na počítači každého uživatele.
  
Ve většině případů automatické škálování funguje podle očekávání v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] verze 2.0 nebo novější. Změny schématu písem však může být problém. Příklad toho, jak to vyřešit, najdete v sekci [postupy: reakce na změny schématu písem ve formulářové aplikaci Windows](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md).
  
## <a name="need-for-automatic-scaling"></a>Potřebu automatické škálování  
Bez automatického měřítka aplikace navržené pro jeden rozlišení nebo písma se buď zobrazí příliš malá nebo příliš velký při změnit řešení nebo písma. Například pokud aplikace je navržená tak, pomocí Tahoma 9 bodu jako základ, bez úpravy zobrazí příliš malá, je-li spustit na počítači, kde je systém písmo Tahoma 12 bodu. Elementy textu, například názvy, nabídek, obsahu textového pole a tak dále vykreslí menší než jiné aplikace. Kromě toho jsou závislé na písmo použité velikosti prvky uživatelského rozhraní (UI), které obsahují text, například záhlaví, nabídky a mnoho ovládacích prvků. V tomto příkladu se zobrazí tyto prvky také relativně menší.

Podobá situace nastane, když aplikace je určená pro určité rozlišení obrazovky. Nejběžnější rozlišení obrazovky je 96 bodů na palec (DPI), který se rovná změna měřítka zobrazení 100 %, ale vyšší řešení zobrazí podpora 125 %, 150 %, 200 % (které v uvedeném pořadí rovna 120, 144 a 192 DPI) a vyšší jsou stále častěji. Bez úpravy, aplikace, zejména na základě grafiky jeden, určený pro jeden řešení se zobrazí příliš velký či příliš malý při spuštění v jiné řešení.

Automatické škálování snaží ameliorate tyto problémy pomocí Automatická změna velikosti formulář a jeho podřízených ovládacích prvků podle relativní velikost písma nebo rozlišení obrazovky. Operační systém Windows podporuje automatické škálování dialogových oken pomocí relativní jednotky měření názvem jednotky dialogu. Jednotky dialogu je založený na systému písma a jeho relaci pixelů může být určen, když funkce Win32 SDK `GetDialogBaseUnits`. Když uživatel změní motiv použitý v systému Windows, všechna dialogová okna jsou automaticky upravována odpovídajícím způsobem. Kromě toho [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] podporuje automatické škálování buď podle na písmo nebo rozlišení obrazovky. Automatické škálování může volitelně zakázán v aplikaci.

## <a name="original-support-for-automatic-scaling"></a>Původní podporu pro automatické škálování
Verze 1.0 a 1.1 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] podporované automatické škálování přehledné tak, aby byla závislá na Windows výchozí písmo použité pro uživatelské rozhraní, reprezentovaný hodnotou Win32 SDK **DEFAULT_GUI_FONT**. Toto písmo je obvykle změnit jenom když se změní rozlišení obrazovky. Implementovat, automatické škálování se používá následující mechanismus:

1. V době návrhu <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> (který je nyní zastaralý) byla nastavena na výšku a šířku písma výchozí systému na počítači pro vývojáře.

2. V době běhu na písmo počítače uživatele byla použita k inicializaci <xref:System.Windows.Forms.Control.Font%2A> vlastnost <xref:System.Windows.Forms.Form> třídy.

3. Před zobrazením formuláře, <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> byla volána metoda škálování formuláře. Tato metoda vypočítat velikost relativní škálování z <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> a <xref:System.Windows.Forms.Control.Font%2A> pak volat <xref:System.Windows.Forms.Control.Scale%2A> metoda ve skutečnosti škálování formulář a jeho podřízených položek.

4. Hodnota <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> byla aktualizována tak to následných volání <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> progresivně velikost formuláře.

Během tento mechanismus je dostatečné pro většinu účelů, která vznikla z následující omezení:

- Vzhledem k tomu <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> vlastnost představuje velikost písma standardních hodnot jako celé číslo hodnoty, dojde k chybám zaokrouhlení, který se ukázalo, když je procházení formuláře pomocí více řešení.

- Automatické škálování byl implementován pouze <xref:System.Windows.Forms.Form> třídy, ne v <xref:System.Windows.Forms.ContainerControl> třídy. Uživatelské ovládací prvky v důsledku toho by škálovat správně jenom v případě, že uživatelský ovládací prvek byl vytvořen ve stejném rozlišení jako formulář a byla umístěny do formuláře v době návrhu.

- Formulářů a jejich podřízené ovládací prvky může být současně určen pouze několik vývojáři pokud jejich počítač řešení byly stejné. Podobně se rovněž dědičnosti formuláře závislé na rozlišení přidružené nadřazeného formuláře.

- Není kompatibilní s novější rozložení manažery zavedené [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] verze 2.0, jako například <xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel>.

- Nepodporoval škálování podle rozlišení zobrazení, která je požadována pro kompatibilita s [!INCLUDE[compact](../../../includes/compact-md.md)].

I když se tento mechanismus zachová [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] verze 2.0 pro zachování zpětné kompatibility, byla nahrazena robustnější škálování mechanismus popsána dále. V důsledku toho <xref:System.Windows.Forms.Form.AutoScale%2A>, <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A>a určité <xref:System.Windows.Forms.Control.Scale%2A> přetížení jsou označeny jako zastaralé.

> [!NOTE]
> Odkazy na těchto členů můžete bezpečně odstranit, při upgradu starší verze kódu na [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] verze 2.0.

## <a name="current-support-for-automatic-scaling"></a>Aktuální podporu pro automatické škálování
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Verze 2.0 surmounts předchozí omezení zavedením následující změny k automatické škálování Windows Forms:

- Základní podpora škálování byl přesunut do <xref:System.Windows.Forms.ContainerControl> třídy tak, aby formulářů, nativní složené ovládací prvky a uživatelské ovládací prvky všechny získat uniform škálování podporu. Nové členy <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> a <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> byly přidány.

- <xref:System.Windows.Forms.Control> Třída také obsahuje několik nových členů, umožňujících účastnit škálování a pro podporu ve smíšeném škálování na stejném tvaru. Konkrétně <xref:System.Windows.Forms.Control.Scale%2A>, <xref:System.Windows.Forms.Control.ScaleChildren%2A>, a <xref:System.Windows.Forms.Control.GetScaledBounds%2A> příjmu podporují členy.

- Pro škálování podle rozlišení obrazovky byla přidána podpora, aby doplňovala systémovou podporu písma, podle definice <xref:System.Windows.Forms.AutoScaleMode> výčtu. Tento režim je kompatibilní s automatického škálování nepodporuje [!INCLUDE[compact](../../../includes/compact-md.md)] povolení jednodušší migrace aplikací.

- Kompatibilita s rozložení manažery, jako <xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel> byl přidán do implementace automatické škálování.

- Škálování faktory jsou nyní představena jako plovoucí hodnoty bodu, obvykle pomocí <xref:System.Drawing.SizeF> struktury zaokrouhlovací chyby prakticky odstranilo.

> [!CAUTION]
> Libovolný různých DPI a písma škálování režimy nejsou podporovány. I když můžete škálovat uživatelského ovládacího prvku pomocí jeden režim (například DPI) a umístěte ji na použití jiného režimu (písma) bez problémů, ale kombinování základní formulář v jeden režim formuláře a odvozené formuláře v jiném může vést k neočekávaným výsledkům.

### <a name="automatic-scaling-in-action"></a>Automatická změna měřítka v akci
Windows Forms teď používá následující logice automaticky škálovat formulářů a jejich obsah:

1. V době návrhu každé <xref:System.Windows.Forms.ContainerControl> zaznamenává škálování režimu a aktuální řešení v <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> a <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, v uvedeném pořadí.

2. V době běhu je uložený na skutečná řešení v <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> vlastnost. <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> Vlastnost dynamicky vypočítá poměr mezi běhu a návrhu škálování rozlišení.

3. Při načtení formuláře, pokud hodnoty <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> a <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> se liší, pak se <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> metoda je volána škálování ovládacího prvku a její podřízené položky. Tato metoda pozastaví rozložení a počet volání <xref:System.Windows.Forms.Control.Scale%2A> metodu za účelem skutečné škálování. Pak se hodnota <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> je aktualizovány k vyloučení progresivní škálování.

4. <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> je také automaticky vyvolá v následujících situacích:

    - V reakci <xref:System.Windows.Forms.Control.OnFontChanged%2A> událost, pokud je režim škálování <xref:System.Windows.Forms.AutoScaleMode.Font>.
  
    - Když se v zjistí rozložení Obnoví řízení kontejneru a změnu <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> nebo <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> vlastnosti.
  
    - Jako implicitní výše, pokud nadřazený <xref:System.Windows.Forms.ContainerControl> bude změněno měřítko. Každý kontejner ovládací prvek je zodpovědná za škálování podřízené pomocí vlastní škálování faktory a není jeden z jeho nadřazený kontejner.

5. Podřízené ovládací prvky můžete změnit jejich chování škálování několika způsoby:

    - <xref:System.Windows.Forms.Control.ScaleChildren%2A> Vlastnost může být potlačena za účelem určení, pokud jejich podřízené ovládací prvky by měla být změněna nebo ne.

    - <xref:System.Windows.Forms.Control.GetScaledBounds%2A> Metoda může být potlačena za účelem upravit hranice, které je ovládací prvek rozšířit, aby, ale není logice škálování.

    - <xref:System.Windows.Forms.Control.ScaleControl%2A> Metoda může být potlačena za účelem změnit škálování logiku pro aktuální ovládací prvek.

## <a name="see-also"></a>Viz také:
 <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>  
 <xref:System.Windows.Forms.Control.Scale%2A>  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>  
 [Vykreslování ovládacích prvků s vizuálními styly](./controls/rendering-controls-with-visual-styles.md)  
 [Postupy: Zvýšení výkonu zabráněním automatické změně měřítka](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)
