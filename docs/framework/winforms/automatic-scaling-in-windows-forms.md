---
title: Automatické škálování
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: 96dbbb5ed20027e25f1bde89748710766ec06506
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732373"
---
# <a name="automatic-scaling-in-windows-forms"></a>Automatické škálování v model Windows Forms

Automatické škálování umožňuje formulář a jeho ovládací prvky, které jsou navržené na jednom počítači s určitým rozlišením obrazovky nebo systémovým písmem, aby se správně zobrazovaly na jiném počítači s jiným rozlišením obrazovky nebo systémovým písmem. Zaručuje, že formulář a jeho ovládací prvky budou inteligentně měnit, aby byly konzistentní s nativními okny a dalšími aplikacemi na počítačích uživatelů i jiných vývojářů. Podpora .NET Framework pro automatické škálování a vizuální styly umožňuje aplikacím .NET Framework udržovat konzistentní vzhled a chování v porovnání s nativními aplikacemi pro Windows na počítači každého uživatele.

Pro většinu částí funguje automatické škálování podle očekávání v .NET Framework verze 2,0 a novější. Změny schématu písem ale můžou být problematické. Příklad toho, jak tento problém vyřešit, najdete v tématu [How to: reagovat na změny schématu písem v aplikaci model Windows Forms](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md).

## <a name="need-for-automatic-scaling"></a>Nutnost automatického škálování

Bez automatického škálování se aplikace navržená pro jedno rozlišení obrazovky nebo písmo při změně rozlišení nebo písma buď příliš malá, nebo je příliš velká. Například pokud je aplikace navržena pomocí formátu Tahoma 9 Point jako směrného plánu, bez úprav se tato hodnota bude zobrazovat příliš malá, pokud bude systém v počítači, kde je písmo systému Tahoma 12 Point. Textové prvky, jako jsou názvy, nabídky, obsah textového pole a tak dále, budou vykresleny méně než jiné aplikace. Kromě toho je velikost prvků uživatelského rozhraní (UI), které obsahují text, například záhlaví, nabídky a mnoho ovládacích prvků, závislá na použitém písmu. V tomto příkladu se tyto prvky zobrazují i relativně menší.

K podobné situaci dojde, když je aplikace navržena pro určité rozlišení obrazovky. Nejběžnějším rozlišením displeje je 96 bodů na palec (DPI), které se rovná 100% velikosti zobrazení, ale vyšší rozlišení zobrazuje podporu 125%, 150%, 200% (v uvedeném pořadí = 120, 144 a 192 DPI) a vyšší se často častěji. Bez úpravy se aplikace, zejména grafika založená na grafice, určená pro jedno rozlišení, bude při spuštění v jiném rozlišení zobrazovat buď příliš velká, nebo příliš malá.

Automatické škálování vyhledá tyto problémy tím, že automaticky změní velikost formuláře a jeho podřízených ovládacích prvků podle relativní velikosti písma nebo rozlišení obrazovky. Operační systém Windows podporuje automatické škálování dialogových oken pomocí relativní jednotky měření označované jako jednotky dialogu. Jednotka dialogového okna je založena na písmu systému a jeho vztahu k pixelům lze určit i v případě, že funkce Win32 SDK `GetDialogBaseUnits`. Když uživatel změní motiv používaný systémem Windows, všechna dialogová okna se odpovídajícím způsobem automaticky upraví. Kromě toho .NET Framework podporuje automatické škálování buď podle výchozího systémového písma, nebo podle rozlišení obrazovky. V případě potřeby je možné automatické škálování zakázat v aplikaci.

## <a name="original-support-for-automatic-scaling"></a>Původní podpora automatického škálování

Verze 1,0 a 1,1 .NET Framework podporují automatické škálování jednoduchým způsobem, který byl závislý na výchozím písmu systému Windows použitém pro uživatelské rozhraní reprezentované hodnotou sady Win32 SDK **DEFAULT_GUI_FONT**. Toto písmo se obvykle mění pouze v případě, že se změní rozlišení zobrazení. Následující mechanismus se použil k implementaci automatického škálování:

1. V době návrhu byl vlastnost <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> (která je nyní zastaralá) nastavená na výšku a šířku výchozího systémového písma v počítači vývojáře.

2. Za běhu se pro inicializaci vlastnosti <xref:System.Windows.Forms.Control.Font%2A> třídy <xref:System.Windows.Forms.Form> použilo výchozí systémové písmo počítače uživatele.

3. Před zobrazením formuláře byla volána metoda <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> pro horizontální navýšení kapacity formuláře. Tato metoda vypočítala relativní velikosti stupnice od <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> a <xref:System.Windows.Forms.Control.Font%2A> pak se zavolala metoda <xref:System.Windows.Forms.Control.Scale%2A> pro skutečnou škálu formuláře a jejích podřízených prvků.

4. Hodnota <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> byla aktualizována, aby následné výzvy pro <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> neměnily velikost formuláře.

I když byl tento mechanismus dostačující pro většinu účelů, utrpělo se z následujících omezení:

- Vzhledem k tomu, že vlastnost <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> představuje velikost písma směrného plánu jako celočíselné hodnoty, dojde k chybám zaokrouhlení, které se stanou zjevné, když je formulář cyklicky více rozlišeními.

- Automatické škálování bylo implementováno pouze v třídě <xref:System.Windows.Forms.Form>, nikoli ve třídě <xref:System.Windows.Forms.ContainerControl>. V důsledku toho se uživatelské ovládací prvky budou škálovat správně pouze v případě, že uživatelský ovládací prvek byl navržen ve stejném rozlišení jako formulář a byl umístěn ve formě v době návrhu.

- Formuláře a jejich podřízené ovládací prvky můžou být souběžně navržené více vývojáři, pokud jejich řešení počítače jsou stejná. Podobně také došlo k dědění formuláře závislého na řešení, které je přidruženo k nadřazenému formuláři.

- Není kompatibilní s novějšími správci rozložení zavedenými ve verzi .NET Framework 2,0, například <xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel>.

- Nepodporuje škálování na základě přímo na rozlišení obrazovky, které se vyžaduje pro kompatibilitu prostředí .NET Compact Framework.

I když je tento mechanismus zachován v .NET Framework verze 2,0 pro zachování zpětné kompatibility, byl nahrazen robustnějším mechanismem škálování popsaným dále. V důsledku toho jsou <xref:System.Windows.Forms.Form.AutoScale%2A>, <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A>a určitá <xref:System.Windows.Forms.Control.Scale%2A> přetížení označena jako zastaralá.

> [!NOTE]
> Odkazy na tyto členy můžete bezpečně odstranit při upgradu starší verze kódu na verzi .NET Framework 2,0.

## <a name="current-support-for-automatic-scaling"></a>Aktuální podpora automatického škálování

.NET Framework verze 2,0 surmounts předchozí omezení tím, že zavádí následující změny automatického škálování model Windows Forms:

- Základní podpora pro škálování byla přesunuta do třídy <xref:System.Windows.Forms.ContainerControl> tak, aby formuláře, nativní složené ovládací prvky a uživatelské ovládací prvky dostaly podporu jednotného škálování. Nové členy <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> a <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> byly přidány.

- Třída <xref:System.Windows.Forms.Control> má také několik nových členů, které jim umožňují zapojit se do škálování a podporovat smíšené škálování na stejném formuláři. Konkrétně členové <xref:System.Windows.Forms.Control.Scale%2A>, <xref:System.Windows.Forms.Control.ScaleChildren%2A>a <xref:System.Windows.Forms.Control.GetScaledBounds%2A> podporují škálování.

- Byla přidána podpora škálování na základě rozlišení obrazovky, která doplňuje systémovou podporu písma, jak je definováno výčtem <xref:System.Windows.Forms.AutoScaleMode>. Tento režim je kompatibilní s automatickým škálováním, které podporuje prostředí .NET Compact Framework umožňující snazší migraci aplikací.

- K implementaci automatického škálování se přidala kompatibilita s správci rozložení, jako je <xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel>.

- Faktory škálování se nyní reprezentují jako hodnoty s plovoucí desetinnou čárkou, obvykle pomocí <xref:System.Drawing.SizeF> struktury, aby byly chyby zaokrouhlení prakticky eliminovány.

> [!CAUTION]
> Nepodporují se libovolné směsi režimů DPI a škálování písma. I když můžete škálovat uživatelský ovládací prvek pomocí jednoho režimu (například DPI) a umístit ho do formuláře pomocí jiného režimu (Font) bez problémů, ale kombinace základního formuláře v jednom režimu a odvozeného formuláře v jiném může vést k neočekávaným výsledkům.

### <a name="automatic-scaling-in-action"></a>Automatické škálování v akci

Model Windows Forms teď používá následující logiku k automatickému škálování formulářů a jejich obsahu:

1. V době návrhu každý <xref:System.Windows.Forms.ContainerControl> zaznamenává režim škálování a aktuální rozlišení v <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> a <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, v uvedeném pořadí.

2. V době běhu je skutečné řešení uloženo ve vlastnosti <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A>. Vlastnost <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> dynamicky vypočítá poměr mezi řešením runtime a škálování v době návrhu.

3. Když se formulář načte, pokud se hodnoty <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> a <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> liší, pak je volána metoda <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> pro horizontální navýšení kapacity ovládacího prvku a jeho podřízených objektů. Tato metoda pozastaví rozložení a zavolá metodu <xref:System.Windows.Forms.Control.Scale%2A> k provedení skutečného škálování. Následně je hodnota <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> aktualizována, aby nedocházelo k progresivnímu škálování.

4. <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> je také automaticky vyvolán v následujících situacích:

    - V reakci na událost <xref:System.Windows.Forms.Control.OnFontChanged%2A>, pokud je režim škálování <xref:System.Windows.Forms.AutoScaleMode.Font>.

    - Když se obnoví rozložení ovládacího prvku kontejner a ve vlastnostech <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> nebo <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> se zjistí změna.

    - Jak je uvedeno výše, když se škáluje nadřazený <xref:System.Windows.Forms.ContainerControl>. Každý ovládací prvek kontejneru zodpovídá za změnu měřítka svých podřízených prvků pomocí vlastních faktorů škálování a nikoli z nadřazeného kontejneru.

5. Podřízené ovládací prvky mohou změnit jejich chování při škálování prostřednictvím několika způsobů:

    - Vlastnost <xref:System.Windows.Forms.Control.ScaleChildren%2A> lze přepsat, chcete-li určit, zda mají být jejich podřízené ovládací prvky zvětšeny.

    - Metodu <xref:System.Windows.Forms.Control.GetScaledBounds%2A> lze přepsat, chcete-li upravit hranice, na které je ovládací prvek zvětšen, ale nikoli logiku škálování.

    - Metodu <xref:System.Windows.Forms.Control.ScaleControl%2A> lze přepsat, chcete-li změnit logiku škálování pro aktuální ovládací prvek.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>
- <xref:System.Windows.Forms.Control.Scale%2A>
- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>
- [Vykreslování ovládacích prvků s vizuálními styly](./controls/rendering-controls-with-visual-styles.md)
- [Postupy: Zvýšení výkonu zabráněním automatické změně měřítka](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)
