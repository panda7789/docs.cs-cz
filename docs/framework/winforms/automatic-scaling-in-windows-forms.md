---
title: Automatická změna měřítka ve Windows Forms
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: 4902cd8ab97771f75e5421a9de7ed1150a7443a8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586580"
---
# <a name="automatic-scaling-in-windows-forms"></a>Automatická změna měřítka ve Windows Forms

Automatické škálování umožňuje formuláře a jejích ovládacích prvků, navržená na jeden počítač s určité zobrazení řešení nebo systémové písmo, odpovídajícím způsobem zobrazený na jiný počítač s jiným zobrazením systému nebo rozlišení písma. Který zajišťuje formuláře a jejích ovládacích prvků bude inteligentně mění svou velikost tak být konzistentní s nativní windows a další aplikace v počítačích uživatelů i ostatní vývojáři. Podpora rozhraní .NET Framework pro automatické škálování a vizuální styly umožňuje aplikacím rozhraní .NET Framework udržovat konzistentní vzhled a chování ve srovnání s nativních aplikací Windows pro každého uživatele počítače.

Ve většině případů automatické škálování funguje podle očekávání v rozhraní .NET Framework verze 2.0 a vyšší. Změny schématu písem však může být problematické. Příklad toho, jak tento problém vyřešit, najdete v části [jak: Reakce na změny schématu písem ve formulářové aplikaci Windows](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md).

## <a name="need-for-automatic-scaling"></a>Potřebu automatické škálování

Bez automatického škálování aplikace navržené pro rozlišení jednoho zobrazení nebo písmo buď zobrazí příliš malá nebo příliš velké při změně písma nebo rozlišení. Například pokud je aplikace navržena pomocí bodu Tahoma 9 jako základ, bez úprav zobrazí příliš malá, je-li spustit na počítači, kde je bod Tahoma 12 systémové písmo. Vykreslí textové prvky, jako jsou názvy, nabídky, obsahu textového pole a tak dále se menší než jiné aplikace. Kromě toho jsou závislé na písmo použité velikosti prvky uživatelského rozhraní (UI), které obsahují text, například záhlaví, nabídky a mnoho ovládacích prvků. V tomto příkladu se zobrazí tyto prvky také relativně menší.

Podobná situace nastane, pokud aplikace je navržená pro určité rozlišení obrazovky. Nejběžnější rozlišení zobrazení je 96 bodů na palec (DPI), který se rovná 100 % měřítko zobrazení, ale podpora 125 %, 150 %, 200 % vyšším rozlišením (které respektive rovná 120, 144 a 192 DPI) a výše jsou stále Častějším řešením. Bez úprav, aplikace, zejména na základě grafiky některou, navržená pro řešení jedné zobrazí příliš velký či příliš malý při spuštění v jiné řešení.

Automatické škálování se snaží zmírnit tyto problémy automaticky změnou velikosti, tvaru a jeho podřízených ovládacích prvků podle relativní velikost písma nebo rozlišení. Operační systém Windows podporuje automatické škálování pomocí relativní měrnou jednotku volá jednotky dialogu dialogových oknech. Jednotky dialogu je založená na systémové písmo a jejich vztah k pixelů může být určen ale funkci Win32 SDK `GetDialogBaseUnits`. Když uživatel změní motiv použitý ve Windows, všechna dialogová okna jsou automaticky upravována odpovídajícím způsobem. Rozhraní .NET Framework navíc podporuje automatické škálování, buď podle výchozí systémové písmo nebo rozlišení obrazovky. Automatické škálování je Volitelně můžete zakázat v aplikaci.

## <a name="original-support-for-automatic-scaling"></a>Původní podporu pro automatické škálování

Verze 1.0 a 1.1 rozhraní .NET Framework podporován automatické škálování v přímočarým způsobem, který byl závislý na Windows výchozí písmo použité pro uživatelské rozhraní, reprezentovaný hodnotou Win32 SDK **DEFAULT_GUI_FONT**. Toto písmo je obvykle změnit jenom při změně rozlišení obrazovky. Následující mechanismu, který byl použit k implementaci automatického škálování:

1. V době návrhu <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> (který je nyní zastaralý) byla nastavena na výšku a šířku výchozí systémové písmo na počítači pro vývojáře.

2. Za běhu, výchozí systémové písmo počítač uživatele byla použita k inicializaci <xref:System.Windows.Forms.Control.Font%2A> vlastnost <xref:System.Windows.Forms.Form> třídy.

3. Před zobrazením formuláři <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> byla volána metoda škálování formuláře. Tato metoda počítá relativní škálování pohybuje od <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> a <xref:System.Windows.Forms.Control.Font%2A> pak volá <xref:System.Windows.Forms.Control.Scale%2A> metoda ve skutečnosti škálování formuláře a jejích potomků.

4. Hodnota <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> byla aktualizována tak to následných volání <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> postupně velikost formuláře.

Během tohoto mechanismu je dostatečné pro většinu účelů, kde z následující omezení:

- Vzhledem k tomu, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> vlastnost představuje velikost písma směrného plánu jako celočíselné hodnoty, dojde k zaokrouhlovací chyby, která se ukázalo, když je formulář cyklicky řešení více rozlišení.

- Automatické škálování byla implementována pouze <xref:System.Windows.Forms.Form> třídy, nikoli v <xref:System.Windows.Forms.ContainerControl> třídy. Uživatelské ovládací prvky v důsledku toho případném vertikálním správně pouze v případě, že uživatelský ovládací prvek byl vytvořen ve stejném rozlišení jako formulář a byl umístěn ve formuláři v době návrhu.

- Formuláře a jejich podřízených ovládacích prvků může být současně určen pouze od více vývojářů jejich počítače řešení byly stejné. Podobně je rovněž dědičnosti formuláře závisí na rozlišení přidružené nadřazeného formuláře.

- Není kompatibilní s novější správci rozložení nepředchází funkce rozhraní .NET Framework verze 2.0, jako například <xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel>.

- Nepodporovalo škálování přímo na rozlišení obrazovky, která je nutná pro kompatibilitu na základě [!INCLUDE[compact](../../../includes/compact-md.md)].

I když tento mechanismus je zachováno v rozhraní .NET Framework verze 2.0 pro zachování zpětné kompatibility, to bylo nahrazeno robustnější mechanismus škálování je popsáno dále. V důsledku toho <xref:System.Windows.Forms.Form.AutoScale%2A>, <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A>a některé <xref:System.Windows.Forms.Control.Scale%2A> přetížení jsou označeny jako zastaralé.

> [!NOTE]
> Odkazy na tyto členy můžete bezpečně odstranit při upgradu starší verze kódu na rozhraní .NET Framework verze 2.0.

## <a name="current-support-for-automatic-scaling"></a>Aktuální podporu pro automatické škálování

Rozhraní .NET Framework verze 2.0 surmounts z předchozích omezení zavedením následujících změn na automatické škálování formuláře Windows:

- Byl přesunut do základní podporu pro škálování <xref:System.Windows.Forms.ContainerControl> třídy tak, aby formulářů, nativní složených ovládacích prvků a uživatelských ovládacích prvků všechny získat jednotné škálování podporu. Nové členy <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> a <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> byly přidány.

- <xref:System.Windows.Forms.Control> Třída také obsahuje několik nových členů, které mohla účastnit škálování a podporovat smíšené škálování ve stejném formuláři. Konkrétně <xref:System.Windows.Forms.Control.Scale%2A>, <xref:System.Windows.Forms.Control.ScaleChildren%2A>, a <xref:System.Windows.Forms.Control.GetScaledBounds%2A> členy podporují škálování.

- Pro škálování na základě rozlišení obrazovky byla přidána podpora k doplnění podpory písma systému, podle definice <xref:System.Windows.Forms.AutoScaleMode> výčtu. Tento režim je kompatibilní s automatického škálování nepodporuje [!INCLUDE[compact](../../../includes/compact-md.md)] povolení je snazší migrace aplikací.

- Kompatibilita s správci rozložení, jako <xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel> byla přidána k implementaci automatického škálování.

- Škálování faktory jsou nyní představena jako hodnoty plovoucího bodu, obvykle s využitím <xref:System.Drawing.SizeF> struktury tak, že chyby zaokrouhlení prakticky odstranilo.

> [!CAUTION]
> Libovolné směsi DPI a písma škálování režimy nejsou podporovány. I když se může škálovat uživatelského ovládacího prvku pomocí jeden režim (například DPI) a umístěte ho na formulář pomocí jiného režimu (písma) bez problémů, ale kombinace základní formulář v nástrojích pro jeden režim a odvozený formulář v nástrojích pro jiný může vést k neočekávaným výsledkům.

### <a name="automatic-scaling-in-action"></a>Automatické škálování v akci

Windows Forms nyní používá následující logiku pro automatické škálování formulářů a jejich obsah:

1. V době návrhu každý <xref:System.Windows.Forms.ContainerControl> zaznamenává škálování režimu a v aktuálním řešení <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> a <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>v uvedeném pořadí.

2. V době běhu, aktuální řešení je uložen v <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> vlastnost. <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> Vlastnost dynamicky vypočítá poměr mezi řešení škálování za běhu a návrhu.

3. Při načtení formuláře, pokud hodnoty <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> a <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> se liší, pak bude <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> metoda je volána škálování ovládacím prvkem a jeho podřízené položky. Tato metoda pozastaví rozložení a volání <xref:System.Windows.Forms.Control.Scale%2A> metodu za účelem skutečné škálování. Potom se hodnota <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> je aktualizovány k vyloučení progresivní škálování.

4. <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> je také automaticky vyvolána v následujících situacích:

    - V reakci <xref:System.Windows.Forms.Control.OnFontChanged%2A> událost, pokud je režim škálování <xref:System.Windows.Forms.AutoScaleMode.Font>.

    - Když se zjistí rozložení obnoví ovládací prvek kontejneru a změnu u <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> nebo <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> vlastnosti.

    - Jako implicitní výše, když nadřazený <xref:System.Windows.Forms.ContainerControl> se mění velikost. Každý ovládací prvek kontejneru je zodpovědná za škálování své podřízené objekty pomocí vlastní škálování faktorů a není jeden z jeho nadřazeného kontejneru.

5. Podřízené ovládací prvky můžete změnit jejich chování škálování několika způsoby:

    - <xref:System.Windows.Forms.Control.ScaleChildren%2A> Vlastnost může být potlačena za účelem určení, pokud jejich podřízených ovládacích prvků má být nastaveno měřítko nebo ne.

    - <xref:System.Windows.Forms.Control.GetScaledBounds%2A> Metoda může být potlačena za účelem upravit hranice, které ovládací prvek je škálovat, aby, ale ne škálování logiku.

    - <xref:System.Windows.Forms.Control.ScaleControl%2A> Metoda může být potlačena za účelem změnit škálování logiku pro aktuální ovládací prvek.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>
- <xref:System.Windows.Forms.Control.Scale%2A>
- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>
- [Vykreslování ovládacích prvků s vizuálními styly](./controls/rendering-controls-with-visual-styles.md)
- [Postupy: Zvýšení výkonu zabráněním automatické změně měřítka](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)
