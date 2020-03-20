---
title: WPF a Windows Forms interop
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 76d1e97c92946267aa1217f52c93594fb63d20de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187154"
---
# <a name="wpf-and-windows-forms-interoperation"></a>Vzájemná spolupráce subsystémů WPF a Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a Windows Forms představují dvě různé architektury pro vytváření aplikačních rozhraní. Obor <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> názvů poskytuje třídy, které umožňují běžné scénáře vzájemné spolupráce. Dvě klíčové třídy, které <xref:System.Windows.Forms.Integration.WindowsFormsHost> implementují možnosti spolupráce jsou a <xref:System.Windows.Forms.Integration.ElementHost>. Toto téma popisuje, které scénáře spolupráce jsou podporovány a které scénáře nejsou podporovány.  
  
> [!NOTE]
> Zvláštní pozornost je věnována *scénáři hybridního řízení.* Hybridní ovládací prvek má ovládací prvek z jedné technologie vnořené v ovládacím prvku z jiné technologie. To se také nazývá *vnořené vzájemné operace*. *Víceúrovňový hybridní ovládací prvek* má více než jednu úroveň vnoření hybridního ovládacího prvku. Příkladem víceúrovňové vnořené spolupráce je ovládací prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows Forms, který obsahuje ovládací prvek, který obsahuje jiný ovládací prvek Windows Forms. Víceúrovňové hybridní ovládací prvky nejsou podporovány.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>
## <a name="hosting-windows-forms-controls-in-wpf"></a>Hostování ovládacích prvků forem systému Windows ve wpf  
 Následující scénáře spolupráce jsou podporovány, pokud [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek hostuje ovládací prvek Windows Forms:  
  
- Ovládací [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvek může být hostitelem jednoho nebo více ovládacích prvků forem systému Windows pomocí jazyka XAML.  
  
- Může být hostitelem jednoho nebo více ovládacích prvků windows forms pomocí kódu.  
  
- Může být hostitelem ovládacích prvků kontejneru Windows Forms, které obsahují jiné ovládací prvky windows forms.  
  
- Může být hostitelem hlavního [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a podrobného formuláře s předlohou a podrobnostmi formulářů systému Windows.  
  
- Může být hostitelem hlavního a podrobného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formuláře s hlavním serverem forů systému Windows a podrobnostmi.  
  
- Může být hostitelem jednoho nebo více ovládacích prvků ActiveX.  
  
- Může být hostitelem jednoho nebo více složených ovládacích prvků.  
  
- Může hostit hybridní [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ovládací prvky pomocí .  
  
- Může hostit hybridní ovládací prvky pomocí kódu.  
  
### <a name="layout-support"></a>Podpora rozložení  
 Následující seznam popisuje známá omezení, <xref:System.Windows.Forms.Integration.WindowsFormsHost> když se prvek pokusí integrovat svůj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostovaný ovládací prvek Windows Forms do systému rozložení.  
  
- V některých případech nelze velikost ovládacích prvků formuláře systému Windows velikost nebo lze jejich velikost pouze na určité dimenze. Například ovládací prvek <xref:System.Windows.Forms.ComboBox> Windows Forms podporuje pouze jednu výšku, která je definována velikostí písma ovládacího prvku. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dynamickérozložení, které předpokládá, že prvky lze <xref:System.Windows.Forms.ComboBox> roztáhnout svisle, hostovaný ovládací prvek nebude roztáhnout podle očekávání.  
  
- Ovládací prvky formuláře systému Windows nelze otočit ani zkosení. Například při otočení uživatelského rozhraní o 90 stupňů, hostované ovládací prvky windows forms zachová jejich vzpřímené poloze.  
  
- Ve většině případů ovládací prvky windows forms nepodporují proporcionální škálování. Přestože celkové rozměry ovládacího prvku bude měřítko, podřízené ovládací prvky a prvky součástí ovládacího prvku nemusí změnit velikost podle očekávání. Toto omezení závisí na tom, jak dobře každý ovládací prvek Windows Forms podporuje škálování.  
  
- V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uživatelském rozhraní můžete změnit pořadí vykreslování prvků a řídit překrývající se chování. Hostovaný ovládací prvek Windows Forms je nakreslena v samostatné HWND, takže je vždy nakreslena nad prvky. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
- Ovládací prvky Windows Forms podporují automatické škálování na základě velikosti písma. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uživatelském rozhraní změna velikosti písma nezmění velikost celého rozložení, i když jednotlivé prvky mohou dynamicky měnit velikost.  
  
### <a name="ambient-properties"></a>Vlastnosti okolí  
 Některé vlastnosti okolí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků mají ekvivalenty windows forms. Tyto vlastnosti okolí jsou rozšířeny na hostované ovládací prvky <xref:System.Windows.Forms.Integration.WindowsFormsHost> windows forms a jsou vystaveny jako veřejné vlastnosti v ovládacím prvku. Ovládací <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek převádí každou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost okolí do ekvivalentního modelu Windows Forms.  
  
 Další informace naleznete v [tématu Windows Forms a WPF Property Mapping](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Chování  
 Následující tabulka popisuje chování spolupráce.  
  
|Chování|Podporuje se|Nepodporuje se|  
|--------------|---------------|-------------------|  
|Průhlednost|Vykreslování ovládacího prvku Windows Forms podporuje průhlednost. Pozadí nadřazeného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku se může stát pozadím hostovaných ovládacích prvků windows forms.|Některé ovládací prvky windows forms nepodporují průhlednost. Například ovládací <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.ComboBox> prvky a nebudou průhledné, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]pokud jsou hostovány společností .|  
|Tabování|Pořadí polí pro hostované ovládací prvky windows forms je stejné jako při hostování těchto ovládacích prvků v aplikaci založené na formulářích systému Windows.<br /><br /> Tabulátor [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] z ovládacího prvku windows forms s klávesou TAB a klávesami SHIFT+TAB funguje obvyklým způsobem.<br /><br /> Ovládací prvky systému Windows Forms, které mají hodnotu <xref:System.Windows.Forms.Control.TabStop%2A> vlastnosti `false` neobdrží fokus, když uživatel karty prostřednictvím ovládacích prvků.<br /><br /> - <xref:System.Windows.Forms.Integration.WindowsFormsHost> Každý ovládací <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> prvek má hodnotu, která určuje, kdy tento <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek obdrží fokus.<br />- Ovládací prvky windows forms, které jsou obsaženy uvnitř kontejneru <xref:System.Windows.Forms.Integration.WindowsFormsHost> postupujte podle pořadí určeného vlastností. <xref:System.Windows.Forms.Control.TabIndex%2A> Tabulátorem z indexu poslední [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] karty umístí fokus na další ovládací prvek, pokud existuje. Pokud neexistuje žádný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jiný ovládací prvek, který lze zaostřit, vrátí se tabulátor do prvního ovládacího prvku Windows Forms v pořadí polí.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>hodnoty pro ovládací <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvky uvnitř jsou relativní k ovládací <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvky windows forms na stejné úrovni, které jsou obsaženy v ovládacím prvku.<br />- Tabování ctí chování specifické pro kontrolu. Například stisknutím klávesy TAB <xref:System.Windows.Forms.TextBox> v ovládacím prvku, který má hodnotu <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> `true` vlastnosti, zadáte kartu do textového pole namísto přesunutí fokusu.|Neužívá se.|  
|Navigace pomocí šipek|- Navigace se šipkami v <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacím prvku je stejná jako v běžném ovládacím prvku kontejneru Windows Forms: Šipka nahoru a ŠIPKA VLEVO vyberte předchozí ovládací prvek a šipka dolů a šipka vpravo vyberte další ovládací prvek.<br />- Klávesy ŠIPKA NAHORU a ŠIPKA VLEVO od <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvního ovládacího prvku, který je obsažen v ovládacím prvku, provádějí stejnou akci jako klávesová zkratka SHIFT+TAB. Pokud je zaostřitelný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek, fokus přesune mimo ovládací prvek. Toto chování se <xref:System.Windows.Forms.ContainerControl> liší od standardní chování v tom, že žádné obtékání na poslední ovládací prvek. Pokud neexistuje žádný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jiný ovládací prvek, který lze zaostřit, fokus se vrátí k poslednímu ovládacímu prvku Windows Forms v pořadí polí.<br />- Šipka dolů a šipka vpravo klávesy <xref:System.Windows.Forms.Integration.WindowsFormsHost> z posledního ovládacího prvku, který je obsažen v ovládacím prvku provést stejnou akci jako klávesa TAB. Pokud je zaostřitelný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek, fokus přesune mimo ovládací prvek. Toto chování se <xref:System.Windows.Forms.ContainerControl> liší od standardní chování v tom, že žádné obtékání na první ovládací prvek. Pokud neexistuje žádný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jiný ovládací prvek, který lze zaostřit, fokus se vrátí k prvnímu ovládacímu prvku Windows Forms v pořadí polí.|Neužívá se.|  
|Akcelerátory|Akcelerátory fungují obvyklým způsobem, s výjimkou případů uvedených ve sloupci "Není podporováno".|Duplicitní akcelerátory napříč technologiemi nefungují jako běžné duplicitní akcelerátory. Pokud je akcelerátor duplikován napříč technologiemi, s alespoň [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jedním v ovládacím prvku Windows Forms a druhým v ovládacím prvku, ovládací prvek Windows Forms vždy obdrží akcelerátor. Fokus nepřepíná mezi ovládacími prvky při stisknutí duplicitního akcelerátoru.|  
|Klávesové zkratky|Klávesové zkratky fungují obvyklým způsobem, s výjimkou případů, kdy je uvedeno ve sloupci "Není podporováno".|- Klávesové zkratky Windows Forms, které jsou zpracovány ve fázi předběžného zpracování, mají vždy přednost před [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klávesovými zkratkami. Pokud máte například <xref:System.Windows.Forms.ToolStrip> definovaný ovládací prvek s klávesovými zkratkami CTRL+S a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Forms.ToolStrip> je příkaz vázán na CTRL+S, obslužná rutina ovládacího prvku je vždy vyvolána jako první, bez ohledu na fokus.<br />- Klávesové zkratky windows <xref:System.Windows.Forms.Control.KeyDown> forms, které jsou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zpracovány událostí jsou zpracovány jako poslední v . Tomuto chování můžete zabránit přepsáním <xref:System.Windows.Forms.Control.IsInputKey%2A> metody ovládacího <xref:System.Windows.Forms.Control.PreviewKeyDown> prvku Windows Forms nebo zpracováním události. `true` Vraťte <xref:System.Windows.Forms.Control.IsInputKey%2A> se z metody nebo <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> nastavte `true` hodnotu <xref:System.Windows.Forms.Control.PreviewKeyDown> vlastnosti v obslužné rutině události.|  
|AcceptsReturn, AcceptsTab a další chování specifické pro ovládací prvek|Vlastnosti, které mění výchozí chování klávesnice, fungují obvyklým <xref:System.Windows.Forms.Control.IsInputKey%2A> způsobem za `true`předpokladu, že ovládací prvek Windows Forms přepíše metodu, která má být vrácena .|Ovládací prvky systému Windows Forms, které mění výchozí chování klávesnice zpracováním <xref:System.Windows.Forms.Control.KeyDown> události, jsou v ovládacím prvku hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zpracovány jako poslední. Vzhledem k tomu, že tyto ovládací prvky jsou zpracovány jako poslední, mohou způsobit neočekávané chování.|  
|Zadat a opustit události|Když fokus nebude obsahující <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek, Enter a Leave události jsou aktivovány <xref:System.Windows.Forms.Integration.WindowsFormsHost> jako obvykle při změně fokusu v jednom ovládacím prvku.|Enter a Leave události nejsou aktivovány, když dojde k následujícím změnám fokusu:<br /><br /> - Zevnitř ven. <xref:System.Windows.Forms.Integration.WindowsFormsHost><br />- Zvenku <xref:System.Windows.Forms.Integration.WindowsFormsHost> do vnitřku ovládacího prvku.<br />- Mimo <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolu.<br />- Z ovládacího prvku Windows <xref:System.Windows.Forms.Integration.WindowsFormsHost> Forms <xref:System.Windows.Forms.Integration.ElementHost> hostovaného v <xref:System.Windows.Forms.Integration.WindowsFormsHost>ovládacím prvku na ovládací prvek hostovaný uvnitř stejné .|  
|Multithreading|Podporovány jsou všechny odrůdy multithreadingu.|Formuláře systému [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows a technologie předpokládají model souběžnosti s jedním podprocesem. Během ladění volání framework objekty z jiných vláken vyvolá výjimku k vynucení tohoto požadavku.|  
|Zabezpečení|Všechny scénáře spolupráce vyžadují úplný vztah důvěryhodnosti.|V částečném vztahu důvěryhodnosti nejsou povoleny žádné scénáře vzájemné spolupráce.|  
|Přístupnost|Všechny scénáře usnadnění jsou podporovány. Produkty asistenční technologie fungují správně, pokud jsou používány pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hybridní aplikace, které obsahují formuláře systému Windows i ovládací prvky.|Neužívá se.|  
|Schránka|Všechny operace schránky fungují obvyklým způsobem. To zahrnuje vyjmutí a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vkládání mezi windows forms a ovládací prvky.|Neužívá se.|  
|Funkce přetažení|Všechny operace přetažení fungují obvyklým způsobem. To zahrnuje operace mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] windows forms a ovládací prvky.|Neužívá se.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>
## <a name="hosting-wpf-controls-in-windows-forms"></a>Hostování ovládacích prvků WPF ve formulářích systému Windows  
 Následující scénáře vzájemné spolupráce jsou podporovány, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] když ovládací prvek Windows Forms hostuje ovládací prvek:  
  
- Hostování jednoho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nebo více ovládacích prvků pomocí kódu.  
  
- Připojování seznamu vlastností s jedním [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nebo více hostovanými ovládacími prvky.  
  
- Hostování jedné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nebo více stránek ve formuláři.  
  
- Spuštění [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okna.  
  
- Hostování hlavního a podrobného formuláře [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s hlavním serverem forem windows forem a podrobnostmi.  
  
- Hostování hlavního a podrobného formuláře s podrobnostmi o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] předloze a formulářích Systému Windows.  
  
- Hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastních ovládacích prvků.  
  
- Hostování hybridních ovládacích prvků.  
  
### <a name="ambient-properties"></a>Vlastnosti okolí  
 Některé vlastnosti okolí ovládacích [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvků Windows Forms mají ekvivalenty. Tyto vlastnosti okolí jsou šířeny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do hostovaných ovládacích <xref:System.Windows.Forms.Integration.ElementHost> prvků a vystaveny jako veřejné vlastnosti v ovládacím prvku. Ovládací <xref:System.Windows.Forms.Integration.ElementHost> prvek překládá každou vlastnost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prostředí Windows Forms na jeho ekvivalentní.  
  
 Další informace naleznete v [tématu Windows Forms a WPF Property Mapping](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Chování  
 Následující tabulka popisuje chování spolupráce.  
  
|Chování|Podporuje se|Nepodporuje se|  
|--------------|---------------|-------------------|  
|Průhlednost|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]vykreslování ovládacích prvku podporuje průhlednost. Pozadí nadřazeného ovládacího prvku Windows [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Forms se může stát pozadím hostovaných ovládacích prvků.|Neužívá se.|  
|Multithreading|Podporovány jsou všechny odrůdy multithreadingu.|Formuláře systému [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows a technologie předpokládají model souběžnosti s jedním podprocesem. Během ladění volání framework objekty z jiných vláken vyvolá výjimku k vynucení tohoto požadavku.|  
|Zabezpečení|Všechny scénáře spolupráce vyžadují úplný vztah důvěryhodnosti.|V částečném vztahu důvěryhodnosti nejsou povoleny žádné scénáře vzájemné spolupráce.|  
|Přístupnost|Všechny scénáře usnadnění jsou podporovány. Produkty asistenční technologie fungují správně, pokud jsou používány pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hybridní aplikace, které obsahují formuláře systému Windows i ovládací prvky.|Neužívá se.|  
|Schránka|Všechny operace schránky fungují obvyklým způsobem. To zahrnuje vyjmutí a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vkládání mezi windows forms a ovládací prvky.|Neužívá se.|  
|Funkce přetažení|Všechny operace přetažení fungují obvyklým způsobem. To zahrnuje operace mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] windows forms a ovládací prvky.|Neužívá se.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Mapování vlastnosti Windows Forms a WPF](windows-forms-and-wpf-property-mapping.md)
