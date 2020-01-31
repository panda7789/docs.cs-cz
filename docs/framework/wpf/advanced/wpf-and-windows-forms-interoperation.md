---
title: Interoperabilita WPF a model Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 5141b84ecd002d920f0d4130bdc2529c0fce4994
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794055"
---
# <a name="wpf-and-windows-forms-interoperation"></a>Vzájemná spolupráce subsystémů WPF a Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a model Windows Forms existují dvě různé architektury pro vytváření aplikačních rozhraní. Obor názvů <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> poskytuje třídy, které umožňují běžné scénáře vzájemné spolupráce. Dvě klíčové třídy, které implementují možnosti spolupráce, jsou <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost>. Toto téma popisuje, které scénáře spolupráce jsou podporovány a které scénáře nejsou podporovány.  
  
> [!NOTE]
> Zvláštní pozornost se věnuje scénáři *hybridního řízení* . Hybridní ovládací prvek má ovládací prvek z jedné technologie, která je vnořená do ovládacího prvku z jiné technologie. Tato funkce se označuje také jako *vnořená mezioperace*. *Víceúrovňový hybridní ovládací prvek* má více než jednu úroveň vnořování hybridních ovládacích prvků. Příkladem vnořené vnořené interaktivní operace je model Windows Forms ovládací prvek, který obsahuje ovládací prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], který obsahuje jiný ovládací prvek model Windows Forms. Víceúrovňové hybridní ovládací prvky se nepodporují.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>Hostování ovládacích prvků model Windows Forms v subsystému WPF  
 Následující scénáře spolupráce jsou podporovány, pokud ovládací prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostuje ovládací prvek model Windows Forms:  
  
- Ovládací prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] může hostovat jeden nebo více model Windows Formsch ovládacích prvků pomocí jazyka XAML.  
  
- Může hostovat jeden nebo více model Windows Formsch ovládacích prvků pomocí kódu.  
  
- Může hostovat ovládací prvky kontejneru model Windows Forms, které obsahují jiné ovládací prvky model Windows Forms.  
  
- Může hostovat hlavní a podrobný formulář s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hlavním serverem a model Windows Forms podrobnosti.  
  
- Může hostovat hlavní a podrobný formulář s model Windows Forms hlavním serverem a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podrobnosti.  
  
- Může hostovat jeden nebo více ovládacích prvků ActiveX.  
  
- Může hostovat jeden nebo více složených ovládacích prvků.  
  
- Může hostovat hybridní ovládací prvky pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
- Může hostovat hybridní ovládací prvky pomocí kódu.  
  
### <a name="layout-support"></a>Podpora rozložení  
 Následující seznam popisuje známá omezení, když se <xref:System.Windows.Forms.Integration.WindowsFormsHost> element pokusí integrovat svůj hostovaný model Windows Forms ovládací prvek do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ho systému rozložení.  
  
- V některých případech nelze změnit velikost model Windows Forms ovládacích prvků, nebo může být velikost nastavena pouze na konkrétní rozměry. Například ovládací prvek model Windows Forms <xref:System.Windows.Forms.ComboBox> podporuje pouze jednu výšku, která je definována velikostí písma ovládacího prvku. Ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dynamické rozložení, které předpokládá, že prvky lze roztáhnout svisle, se hostovaný <xref:System.Windows.Forms.ComboBox> ovládací prvek nebude roztahovat podle očekávání.  
  
- Ovládací prvky model Windows Forms nelze otáčet ani zkosit. Například při otočení uživatelského rozhraní o 90 stupňů, budou hostované model Windows Forms ovládací prvky udržovat svou vzhůru polohu.  
  
- Ve většině případů ovládací prvky model Windows Forms nepodporují proporcionální škálování. I když budou celkové rozměry ovládacího prvku škálované, podřízené ovládací prvky a prvky komponenty ovládacího prvku se nemusí měnit podle očekávání. Toto omezení závisí na tom, jak dobře každý ovládací prvek model Windows Forms podporuje škálování.  
  
- V uživatelském rozhraní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] můžete změnit pořadí vykreslování prvků pro řízení překrývajících se chování. Hostovaný model Windows Forms ovládací prvek je vykreslen v samostatném elementu HWND, takže je vždy vykreslen nad [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky.  
  
- Model Windows Forms ovládací prvky podporují automatické škálování na základě velikosti písma. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]m uživatelském rozhraní změna velikosti písma nemění velikost celého rozložení, i když jednotlivé prvky mohou dynamicky měnit velikost.  
  
### <a name="ambient-properties"></a>Vlastnosti okolí  
 Některé vlastnosti okolí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků mají model Windows Forms ekvivalenty. Tyto vlastnosti okolí jsou šířeny do hostovaných model Windows Forms ovládacích prvků a zpřístupněny jako veřejné vlastnosti v ovládacím prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost>. <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek přeloží každou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ambientních vlastností na jeho ekvivalent model Windows Forms.  
  
 Další informace najdete v tématu [mapování vlastností model Windows Forms a WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Chování  
 Následující tabulka popisuje chování spolupráce.  
  
|Chování|Podporované|Není podporováno|  
|--------------|---------------|-------------------|  
|Průhlednost|Vykreslování ovládacího prvku model Windows Forms podporuje průhlednost. Pozadí nadřazeného ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se může stát pozadím hostovaných model Windows Formsch ovládacích prvků.|Některé ovládací prvky model Windows Forms nepodporují transparentnost. Například <xref:System.Windows.Forms.TextBox> a <xref:System.Windows.Forms.ComboBox> ovládací prvky nebudou transparentní při hostování v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|Procházení tabulátorem|Pořadí karet pro hostované model Windows Forms ovládací prvky je stejné jako při hostování těchto ovládacích prvků v aplikaci založené na model Windows Forms.<br /><br /> Klávesová zkratka ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] k ovládacímu prvku model Windows Forms pomocí klávesy TAB a kláves SHIFT + TAB fungují jako obvykle.<br /><br /> Model Windows Forms ovládací prvky, které mají hodnotu vlastnosti <xref:System.Windows.Forms.Control.TabStop%2A> `false`, nezískají fokus, když jsou na kartě uživatele ovládací prvky.<br /><br /> -Každý ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> má hodnotu <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>, která určuje, kdy tento ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> získá fokus.<br />-Model Windows Forms ovládací prvky, které jsou obsaženy v kontejneru <xref:System.Windows.Forms.Integration.WindowsFormsHost>, odpovídají pořadí určenému vlastností <xref:System.Windows.Forms.Control.TabIndex%2A>. Tabulátory od posledního indexu karet mají fokus na další ovládací prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], pokud nějaký existuje. Pokud žádný jiný ovládací prvek s fokusem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] neexistuje, tabulátor se vrátí k prvnímu ovládacímu prvku model Windows Forms v pořadí ovládacích prvků.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> hodnoty pro ovládací prvky uvnitř <xref:System.Windows.Forms.Integration.WindowsFormsHost> jsou relativní k model Windows Forms ovládací prvky na stejné úrovni, které jsou obsaženy v ovládacím prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />– Na kartách se uplatní chování specifické pro kontrolu. Například stisknutím klávesy TAB v ovládacím prvku <xref:System.Windows.Forms.TextBox>, který má hodnotu vlastnosti <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> `true` zadá do textového pole tabulátor místo přesunutí fokusu.|Nelze použít.|  
|Navigace pomocí kláves se šipkami|-Navigace pomocí šipkových kláves v ovládacím prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost> je stejná jako v běžném ovládacím prvku kontejneru model Windows Forms: klávesy šipka nahoru a šipka vlevo výběr předchozího ovládacího prvku a šipky dolů a šipka vpravo vyberte další ovládací prvek.<br />– Klávesy šipka nahoru a šipka vlevo od prvního ovládacího prvku, který je obsažen v ovládacím prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost>, provádějí stejnou akci jako klávesová zkratka SHIFT + TAB. Pokud je ovládací prvek s fokusem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], fokus se přesune mimo ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Toto chování se liší od standardního chování <xref:System.Windows.Forms.ContainerControl> v tom, že k poslednímu řízení nedochází bez zalomení. Pokud žádný jiný ovládací prvek s fokusem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] neexistuje, fokus se vrátí na poslední ovládací prvek model Windows Forms v pořadí prvků.<br />– ŠIPKY dolů a šipka vpravo od posledního ovládacího prvku, který je obsažen v ovládacím prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost>, provádějí stejnou akci jako Klávesa TAB. Pokud je ovládací prvek s fokusem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], fokus se přesune mimo ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Toto chování se liší od standardního chování <xref:System.Windows.Forms.ContainerControl> v tom, že k prvnímu ovládacímu prvku nedochází bez zalomení. Pokud žádný jiný ovládací prvek s fokusem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] neexistuje, fokus se vrátí na první ovládací prvek model Windows Forms v pořadí prvků.|Nelze použít.|  
|Akcelerátory|Akcelerátory fungují jako obvykle, s výjimkou případů, kdy je uvedeno ve sloupci "Nepodporováno".|Duplicitní akcelerátory napříč technologiemi nefungují jako běžné duplicitní akcelerátory. V případě, že je akcelerátor duplikován napříč technologiemi, s alespoň jedním ovládacím prvkem model Windows Forms a druhým ovládacím prvkem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ovládací prvek model Windows Forms vždy obdrží akcelerátor. Při stisknutí duplicitního akcelerátoru fokus nepřepínání mezi ovládacími prvky.|  
|Klávesové zkratky|Klávesové zkratky pracují jako obvykle, s výjimkou případů, kdy je uvedeno ve sloupci "Nepodporováno".|-Model Windows Forms klávesových zkratek, které jsou zpracovávány ve fázi předzpracování, vždy mají přednost před [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klávesových zkratek. Například pokud máte ovládací prvek <xref:System.Windows.Forms.ToolStrip> s definovanými klávesami CTRL + S a je k dispozici [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] příkaz, který je vázán na kombinaci kláves CTRL + S, obslužná rutina ovládacího prvku <xref:System.Windows.Forms.ToolStrip> je vždy vyvolána jako první, bez ohledu na fokus.<br />-Model Windows Forms klávesových zkratek, které jsou zpracovávány událostí <xref:System.Windows.Forms.Control.KeyDown>, se zpracovávají jako poslední v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Tomuto chování můžete zabránit přepsáním <xref:System.Windows.Forms.Control.IsInputKey%2A> metody ovládacího prvku model Windows Forms nebo zpracováním události <xref:System.Windows.Forms.Control.PreviewKeyDown>. Vraťte `true` z metody <xref:System.Windows.Forms.Control.IsInputKey%2A> nebo nastavte hodnotu vlastnosti <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> na `true` v obslužné rutině události <xref:System.Windows.Forms.Control.PreviewKeyDown>.|  
|AcceptsReturn, AcceptsTabs a další chování specifické pro ovládací prvky|Vlastnosti, které mění výchozí chování klávesnice, fungují obvyklým způsobem za předpokladu, že model Windows Forms ovládací prvek přepisuje metodu <xref:System.Windows.Forms.Control.IsInputKey%2A> a vrátí `true`.|Model Windows Forms ovládací prvky, které mění výchozí chování klávesnice tím, že zpracování události <xref:System.Windows.Forms.Control.KeyDown> zpracovává poslední v ovládacím prvku hostitel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Vzhledem k tomu, že se tyto ovládací prvky zpracovávají jako poslední, můžou způsobit neočekávané chování.|  
|Zadat a opustit události|Pokud fokus nepřejde k ovládacímu prvku, který obsahuje <xref:System.Windows.Forms.Integration.ElementHost>, události Enter a opustit jsou vyvolány obvyklým způsobem při změně fokusu v jednom ovládacím prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|Události Enter a opustit nejsou vyvolány, když dojde k následujícím změnám fokusu:<br /><br /> – Zevnitř k vnějšímu ovládacímu prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />– Od vně k uvnitř ovládacího prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />– Mimo ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />– Z ovládacího prvku model Windows Forms hostovaného v <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacím prvku do ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost> hostovaného ve stejném <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|  
|Multithreading|Podporují se všechny odrůdy s více vlákny.|Technologie model Windows Forms i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] předpokládají model souběžnosti s jedním vláknem. Během ladění volání objektů rozhraní z jiných vláken vyvolá výjimku k vykonání tohoto požadavku.|  
|Zabezpečení –|Všechny scénáře vzájemných operací vyžadují úplný vztah důvěryhodnosti.|V částečném vztahu důvěryhodnosti nejsou povoleny žádné scénáře vzájemných operací.|  
|Usnadnění|Podporují se všechny scénáře přístupnosti. Produkty asistenční technologie fungují správně, pokud jsou používány pro hybridní aplikace, které obsahují ovládací prvky model Windows Forms i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Nelze použít.|  
|Schránka|Všechny operace schránky fungují obvyklým způsobem. To zahrnuje řezání a vkládání mezi ovládacími prvky model Windows Forms a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Nelze použít.|  
|Funkce přetažení|Všechny operace přetažení fungují obvyklým způsobem. To zahrnuje operace mezi ovládacími prvky model Windows Forms a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Nelze použít.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Hostování ovládacích prvků WPF v model Windows Forms  
 Následující scénáře spolupráce jsou podporovány, pokud ovládací prvek model Windows Forms hostuje ovládací prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
- Hostování jednoho nebo více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ch ovládacích prvků pomocí kódu.  
  
- Přidružení seznamu vlastností k jednomu nebo více hostovaným [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacím prvkům.  
  
- Hostování jedné nebo více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránek ve formuláři.  
  
- Spouští se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okno.  
  
- Hostování hlavního nebo podrobného formuláře s model Windows Forms hlavním serverem a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podrobnosti.  
  
- Hostování hlavního nebo podrobného formuláře s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hlavním serverem a model Windows Forms podrobnosti.  
  
- Hostování vlastních ovládacích prvků [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Hostování hybridních ovládacích prvků.  
  
### <a name="ambient-properties"></a>Vlastnosti okolí  
 Některé vlastnosti okolí model Windows Forms ovládacích prvků mají [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekvivalenty. Tyto vlastnosti okolí jsou šířeny do hostovaných [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků a zpřístupněny jako veřejné vlastnosti v ovládacím prvku <xref:System.Windows.Forms.Integration.ElementHost>. <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek přeloží každou model Windows Forms vlastnost Ambient na jeho ekvivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Další informace najdete v tématu [mapování vlastností model Windows Forms a WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Chování  
 Následující tabulka popisuje chování spolupráce.  
  
|Chování|Podporované|Není podporováno|  
|--------------|---------------|-------------------|  
|Průhlednost|vykreslování ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje průhlednost. Pozadí nadřazeného ovládacího prvku model Windows Forms se může stát pozadím hostovaných [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ch ovládacích prvků.|Nelze použít.|  
|Multithreading|Podporují se všechny odrůdy s více vlákny.|Technologie model Windows Forms i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] předpokládají model souběžnosti s jedním vláknem. Během ladění volání objektů rozhraní z jiných vláken vyvolá výjimku k vykonání tohoto požadavku.|  
|Zabezpečení –|Všechny scénáře vzájemných operací vyžadují úplný vztah důvěryhodnosti.|V částečném vztahu důvěryhodnosti nejsou povoleny žádné scénáře vzájemných operací.|  
|Usnadnění|Podporují se všechny scénáře přístupnosti. Produkty asistenční technologie fungují správně, pokud jsou používány pro hybridní aplikace, které obsahují ovládací prvky model Windows Forms i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Nelze použít.|  
|Schránka|Všechny operace schránky fungují obvyklým způsobem. To zahrnuje řezání a vkládání mezi ovládacími prvky model Windows Forms a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Nelze použít.|  
|Funkce přetažení|Všechny operace přetažení fungují obvyklým způsobem. To zahrnuje operace mezi ovládacími prvky model Windows Forms a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Nelze použít.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Mapování vlastnosti Windows Forms a WPF](windows-forms-and-wpf-property-mapping.md)
