---
title: Vzájemná spolupráce subsystémů WPF a Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 0326f283cb271d1578e94b648e423c6f88c579f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917392"
---
# <a name="wpf-and-windows-forms-interoperation"></a>Vzájemná spolupráce subsystémů WPF a Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] existují dvě různé architektury pro vytváření aplikačních rozhraní. <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> Obor názvů poskytuje třídy, které umožňují běžné scénáře vzájemné spolupráce. Dvě klíčové třídy, které implementují možnosti spolupráce, <xref:System.Windows.Forms.Integration.WindowsFormsHost> jsou <xref:System.Windows.Forms.Integration.ElementHost>a. Toto téma popisuje, které scénáře spolupráce jsou podporovány a které scénáře nejsou podporovány.  
  
> [!NOTE]
> Zvláštní pozornost se věnuje scénáři *hybridního řízení* . Hybridní ovládací prvek má ovládací prvek z jedné technologie, která je vnořená do ovládacího prvku z jiné technologie. Tato *funkce*se označuje také jako vnořená mezioperace. *Víceúrovňový hybridní ovládací prvek* má více než jednu úroveň vnořování hybridních ovládacích prvků. Příkladem vnořené vnořené interaktivní operace je [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek, který [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje ovládací prvek, který obsahuje jiný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek. Víceúrovňové hybridní ovládací prvky se nepodporují.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>Hostování ovládacích prvků model Windows Forms v subsystému WPF  
 Následující scénáře spolupráce jsou podporovány, pokud [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek hostuje ovládací prvek model Windows Forms:  
  
- Ovládací prvek může hostovat jeden nebo více [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků pomocí jazyka XAML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
- Může hostovat jeden nebo více [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků pomocí kódu.  
  
- Může hostovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky kontejneru, které obsahují [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jiné ovládací prvky.  
  
- Může hostovat hlavní a podrobný formulář s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hlavním a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] podrobnostem.  
  
- Může hostovat hlavní a podrobný formulář s [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hlavním a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podrobnostem.  
  
- Může hostovat jeden nebo více ovládacích prvků ActiveX.  
  
- Může hostovat jeden nebo více složených ovládacích prvků.  
  
- Může hostovat hybridní ovládací prvky pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
- Může hostovat hybridní ovládací prvky pomocí kódu.  
  
### <a name="layout-support"></a>Podpora rozložení  
 Následující seznam popisuje známá omezení, když se <xref:System.Windows.Forms.Integration.WindowsFormsHost> element pokusí o integraci svého hostovaného [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému rozložení.  
  
- V některých případech [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nelze změnit velikost ovládacích prvků, nebo může být velikost nastavena pouze na konkrétní rozměry. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Například<xref:System.Windows.Forms.ComboBox> ovládací prvek podporuje pouze jednu výšku, která je definována velikostí písma ovládacího prvku. V dynamickém rozložení, které předpokládá, že prvky lze roztáhnout svisle, <xref:System.Windows.Forms.ComboBox> se hostovaný ovládací prvek nebude roztahovat podle očekávání. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ovládací prvky nelze otáčet ani zkosit. Například při otočení uživatelského rozhraní o 90 stupňů budou hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky udržovat svou vzhůru polohu.  
  
- Ve většině případů [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nepodporují proporcionální škálování. I když budou celkové rozměry ovládacího prvku škálované, podřízené ovládací prvky a prvky komponenty ovládacího prvku se nemusí měnit podle očekávání. Toto omezení závisí na tom, jak [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dobře každý ovládací prvek podporuje škálování.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] V uživatelském rozhraní můžete změnit pořadí vykreslování prvků pro řízení překrývajících se chování. Hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek je vykreslený v samostatném [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu HWND, takže je vždy vykreslen nad prvky.  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ovládací prvky podporují automatické škálování na základě velikosti písma. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] V uživatelském rozhraní změna velikosti písma nemění velikost celého rozložení, i když jednotlivé prvky se mohou dynamicky měnit.  
  
### <a name="ambient-properties"></a>Vlastnosti okolí  
 Některé z okolních vlastností [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků mají [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ekvivalenty. Tyto vlastnosti okolí jsou šířeny do hostovaných [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků a zpřístupněny jako veřejné vlastnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku. Ovládací prvek přeloží každou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost okolí na její [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ekvivalent. <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
  
 Další informace najdete v tématu [mapování vlastností model Windows Forms a WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Chování  
 Následující tabulka popisuje chování spolupráce.  
  
|Chování|Podporováno|Není podporováno|  
|--------------|---------------|-------------------|  
|Průhlednost|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]vykreslování ovládacího prvku podporuje průhlednost. Pozadí nadřazeného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku může být pozadím hostovaných [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků.|Některé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nepodporují transparentnost. Například <xref:System.Windows.Forms.TextBox> ovládací prvky a <xref:System.Windows.Forms.ComboBox> nebudou transparentní při hostování nástrojem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|Procházení tabulátorem|Pořadí karet pro hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky je stejné jako v případě, že jsou tyto ovládací [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]prvky hostovány v aplikaci založené na.<br /><br /> Klávesová zkratka [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ovládacíhoprvku s klávesami Tab a klávesy SHIFT + TAB budou fungovat obvyklým způsobem. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ovládací prvky, které <xref:System.Windows.Forms.Control.TabStop%2A> mají `false` hodnotu vlastnosti, nezískají fokus, když jsou na kartě uživatele ovládací prvky.<br /><br /> -Každý <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> má hodnotu, která určuje, kdy <xref:System.Windows.Forms.Integration.WindowsFormsHost> tento ovládací prvek dostane fokus.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ovládací prvky, které jsou obsaženy <xref:System.Windows.Forms.Integration.WindowsFormsHost> v kontejneru, následují pořadí určené <xref:System.Windows.Forms.Control.TabIndex%2A> vlastností. Tabulátory od posledního indexu karet mají fokus na další [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek, pokud nějaký existuje. Pokud neexistuje žádný jiný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek s fokusem, vrátí se tabulátory na první [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek v pořadí prvků.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>hodnoty pro ovládací prvky uvnitř <xref:System.Windows.Forms.Integration.WindowsFormsHost> jsou relativní k ovládacím [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] prvkům stejné úrovně <xref:System.Windows.Forms.Integration.WindowsFormsHost> , které jsou obsaženy v ovládacím prvku.<br />– Na kartách se uplatní chování specifické pro kontrolu. Například stisknutí klávesy TAB v <xref:System.Windows.Forms.TextBox> ovládacím prvku, který <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> má hodnotu `true` vlastnosti, zadá do textového pole tabulátor místo přesunutí fokusu.|Není k dispozici.|  
|Navigace pomocí kláves se šipkami|-Navigace pomocí kláves se šipkami v <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacím prvku je stejná jako v běžném [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacím prvku kontejneru: Klávesa šipka nahoru a šipka dolů vybere předchozí ovládací prvek a šipky dolů a šipka vpravo výběr dalšího ovládacího prvku.<br />– Klávesy šipka nahoru a šipka vlevo od prvního ovládacího prvku, který je obsažen v <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacím prvku, provádějí stejnou akci jako klávesová zkratka SHIFT + TAB. Pokud je k dispozici [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek s fokusem, fokus se přesune <xref:System.Windows.Forms.Integration.WindowsFormsHost> mimo ovládací prvek. Toto chování se liší od standardního <xref:System.Windows.Forms.ContainerControl> chování v tom, že k poslednímu řízení nedochází bez zalomení. Pokud neexistuje žádný jiný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek s fokusem, fokus se vrátí na poslední [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek v pořadí prvků.<br />– Šipky dolů a šipka vpravo od posledního ovládacího prvku, který je obsažen v <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacím prvku, provádějí stejnou akci jako Klávesa TAB. Pokud je k dispozici [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek s fokusem, fokus se přesune <xref:System.Windows.Forms.Integration.WindowsFormsHost> mimo ovládací prvek. Toto chování se liší od standardního <xref:System.Windows.Forms.ContainerControl> chování v tom, že k prvnímu ovládacímu prvku nedochází bez zalomení. Pokud neexistuje žádný jiný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek s fokusem, fokus se vrátí na první [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek v pořadí prvků.|Není k dispozici.|  
|Akcelerátory|Akcelerátory fungují jako obvykle, s výjimkou případů, kdy je uvedeno ve sloupci "Nepodporováno".|Duplicitní akcelerátory napříč technologiemi nefungují jako běžné duplicitní akcelerátory. V případě, že je akcelerátor duplikován napříč technologiemi, s alespoň jedním [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacím prvkem a druhým [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacím prvkem, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek vždy obdrží akcelerátor. Při stisknutí duplicitního akcelerátoru fokus nepřepínání mezi ovládacími prvky.|  
|Klávesové zkratky|Klávesové zkratky pracují jako obvykle, s výjimkou případů, kdy je uvedeno ve sloupci "Nepodporováno".|-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]Klávesové zkratky, které jsou zpracovávány ve fázi předzpracování, vždy mají přednost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] před klávesovými klávesami. Například pokud máte <xref:System.Windows.Forms.ToolStrip> ovládací prvek s definovanou klávesovou zkratkou Ctrl + s a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je k dispozici příkaz, který je vázán na kombinaci kláves CTRL <xref:System.Windows.Forms.ToolStrip> + s, obslužná rutina je vždy vyvolána jako první, bez ohledu na fokus.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]Klávesové zkratky, které jsou zpracovávány <xref:System.Windows.Forms.Control.KeyDown> událostí, jsou zpracovávány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]jako poslední. Tomuto chování můžete zabránit přepsáním [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.IsInputKey%2A> metody ovládacího prvku nebo zpracováním <xref:System.Windows.Forms.Control.PreviewKeyDown> události. Vraťte `true` <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> se `true` z metody nebo nastavte hodnotu vlastnosti na <xref:System.Windows.Forms.Control.PreviewKeyDown> obslužnou rutinu události. <xref:System.Windows.Forms.Control.IsInputKey%2A>|  
|AcceptsReturn, AcceptsTabs a další chování specifické pro ovládací prvky|Vlastnosti, které mění výchozí chování klávesnice, fungují obvyklým způsobem za předpokladu, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] že <xref:System.Windows.Forms.Control.IsInputKey%2A> ovládací prvek Přepisuje `true`metodu, která se má vrátit.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ovládací prvky, které mění výchozí chování <xref:System.Windows.Forms.Control.KeyDown> klávesnice, jsou zpracovávány jako poslední v ovládacím prvku host. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vzhledem k tomu, že se tyto ovládací prvky zpracovávají jako poslední, můžou způsobit neočekávané chování.|  
|Zadat a opustit události|Pokud fokus nepřejde do nadřazeného <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku, události Enter a opustit jsou vyvolány obvyklým způsobem při změně fokusu v rámci jednoho <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.|Události Enter a opustit nejsou vyvolány, když dojde k následujícím změnám fokusu:<br /><br /> – Zevnitř k vnějšímu <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacímu prvku.<br />– Od vnější k uvnitř <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.<br />– Mimo <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek.<br />– Od [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku hostovaného <xref:System.Windows.Forms.Integration.WindowsFormsHost> v ovládacím prvku k <xref:System.Windows.Forms.Integration.ElementHost> ovládacímu prvku hostovanému <xref:System.Windows.Forms.Integration.WindowsFormsHost>v rámci stejného.|  
|Multithreading|Podporují se všechny odrůdy s více vlákny.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Technologie i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] předpokládají model souběžnosti s jedním vláknem. Během ladění volání objektů rozhraní z jiných vláken vyvolá výjimku k vykonání tohoto požadavku.|  
|Zabezpečení|Všechny scénáře vzájemných operací vyžadují úplný vztah důvěryhodnosti.|V částečném vztahu důvěryhodnosti nejsou povoleny žádné scénáře vzájemných operací.|  
|Usnadnění|Podporují se všechny scénáře přístupnosti. Produkty asistenční technologie fungují správně, pokud jsou používány pro hybridní aplikace, které obsahují obojí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.|Není k dispozici.|  
|Schránka|Všechny operace schránky fungují obvyklým způsobem. To zahrnuje vkládání a vkládání mezi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacími prvky a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .|Není k dispozici.|  
|Funkce přetažení|Všechny operace přetažení fungují obvyklým způsobem. To zahrnuje operace mezi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacími prvky.|Není k dispozici.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Hostování ovládacích prvků WPF v model Windows Forms  
 Následující scénáře spolupráce jsou podporovány, pokud ovládací prvek model Windows Forms hostuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek:  
  
- Hostování jednoho nebo více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků pomocí kódu.  
  
- Přidružení seznamu vlastností k jednomu nebo více hostovaným [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacím prvkům.  
  
- Hostování jedné nebo více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránek ve formuláři.  
  
- Spouští se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okno.  
  
- Hostování hlavního nebo podrobného formuláře s [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hlavním a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podrobnostem.  
  
- Hostování hlavního nebo podrobného formuláře s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hlavním a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] podrobnostem.  
  
- Hostování vlastních [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků.  
  
- Hostování hybridních ovládacích prvků.  
  
### <a name="ambient-properties"></a>Vlastnosti okolí  
 Některé z okolních vlastností [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků mají [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekvivalenty. Tyto vlastnosti okolí jsou šířeny do hostovaných [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků a zpřístupněny jako veřejné vlastnosti <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku. Ovládací prvek přeloží každou [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastnost okolí na její [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekvivalent. <xref:System.Windows.Forms.Integration.ElementHost>  
  
 Další informace najdete v tématu [mapování vlastností model Windows Forms a WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Chování  
 Následující tabulka popisuje chování spolupráce.  
  
|Chování|Podporováno|Není podporováno|  
|--------------|---------------|-------------------|  
|Průhlednost|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]vykreslování ovládacího prvku podporuje průhlednost. Pozadí nadřazeného [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku může být pozadím hostovaných [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků.|Není k dispozici.|  
|Multithreading|Podporují se všechny odrůdy s více vlákny.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Technologie i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] předpokládají model souběžnosti s jedním vláknem. Během ladění volání objektů rozhraní z jiných vláken vyvolá výjimku k vykonání tohoto požadavku.|  
|Zabezpečení|Všechny scénáře vzájemných operací vyžadují úplný vztah důvěryhodnosti.|V částečném vztahu důvěryhodnosti nejsou povoleny žádné scénáře vzájemných operací.|  
|Usnadnění|Podporují se všechny scénáře přístupnosti. Produkty asistenční technologie fungují správně, pokud jsou používány pro hybridní aplikace, které obsahují obojí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.|Není k dispozici.|  
|Schránka|Všechny operace schránky fungují obvyklým způsobem. To zahrnuje vkládání a vkládání mezi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacími prvky a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .|Není k dispozici.|  
|Funkce přetažení|Všechny operace přetažení fungují obvyklým způsobem. To zahrnuje operace mezi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacími prvky.|Není k dispozici.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návod: Hostování ovládacího prvku model Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Návod: Hostování model Windows Forms složeného ovládacího prvku v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF v model Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Mapování vlastnosti Windows Forms a WPF](windows-forms-and-wpf-property-mapping.md)
