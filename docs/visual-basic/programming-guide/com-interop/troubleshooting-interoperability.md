---
title: Řešení potíží s interoperabilitou (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop, deploying assemblies
- assemblies [Visual Basic]
- interop, installing assemblies that share components
- COM objects, troubleshooting
- interop, sharing components
- troubleshooting interoperability [Visual Basic]
- interoperability, troubleshooting
- COM interop [Visual Basic], troubleshooting
- assemblies [Visual Basic], deploying
- troubleshooting Visual Basic, interoperability
- interop assemblies
- interoperability, sharing components
- shared components, using with assemblies
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
ms.openlocfilehash: 197361020ad8c6a88a5fc8617b8e24f420799e14
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377218"
---
# <a name="troubleshooting-interoperability-visual-basic"></a>Řešení potíží s interoperabilitou (Visual Basic)
Při spolupráci mezi modelem COM a spravovaný kód [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], mohou nastat jeden nebo více z těchto běžných problémů.  
  
## <a name="vbconinteroperabilitymarshalinganchor1"></a> Zařazování spolupráce  
 V některých případech bude pravděpodobně nutné použít datové typy, které nejsou součástí [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Sestavení vzájemné spolupráce zpracovat většinu práce s objekty COM, ale možná budete muset určit datové typy, které se používají při spravované objekty jsou vystaveny objektům modelu COM. Například musíte zadat struktury v knihovnách tříd `BStr` nespravovaný typ na řetězce zaslána com. objekty vytvořené pomocí jazyka Visual Basic 6.0 a starší verze. V takovém případě můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut způsobí spravované typy zpřístupní jako nespravované typy.  
  
## <a name="vbconinteroperabilitymarshalinganchor2"></a> Export řetězce pevné délky na nespravovaný kód  
 V jazyce Visual Basic verze 6.0 a starší jsou exportovány řetězců na objekty modelu COM jako sekvence bajtů bez ukončení hodnotou null znaků. Z důvodu kompatibility s jinými jazyky Visual Basic .NET obsahuje znak ukončení při exportu řetězce. Nejlepší způsob, jak vyřešit k této nekompatibilitě je exportovat řetězce, které chybí ukončovací znak jako pole `Byte` nebo `Char`.  
  
## <a name="vbconinteroperabilitymarshalinganchor3"></a> Export hierarchie dědičnosti  
 Spravované třídy, které hierarchie sloučit si při vystavení jako objekty modelu COM. Například pokud definujete základní třídu se členem a potom dědit základní třídy v odvozené třídě, která je vystavena jako objekt modelu COM, klienty, kteří používají odvozené třídy v objektu modelu COM nebudou moct používat zděděné členy. Členy základní třídy je přístupný z objektů COM pouze jako instance základní třídy a pak pouze v případě, že základní třídy se také vytvoří jako objekt modelu COM.  
  
## <a name="overloaded-methods"></a>Přetížené metody  
 I když přetížené metody můžete vytvořit pomocí jazyka Visual Basic, nejsou podporovány modelu COM. Když je třídu, která obsahuje přetížené metody vystaveny jako objekt modelu COM, nové názvy metod jsou generovány pro přetížené metody.  
  
 Představte si třeba třídu, která má dvě přetížení `Synch` metody. Pokud třída je vystavená jako objekt modelu COM, může být nové názvy vytvořena metoda `Synch` a `Synch_2`.  
  
 Přejmenování může způsobit dva problémy pro spotřebitele objektu COM.  
  
1.  Klienti nemusí očekávat, že názvy vytvořena metoda.  
  
2.  Vytvořena metoda názvy ve třídě vystavena jako objekt modelu COM lze změnit nová přetížení se přidají do třídy nebo její základní třídě. To může způsobit problémy se správou verzí.  
  
 K řešení problémů, obě, zadejte jednotlivé metody jedinečný název, namísto použití přetížení, při vývoji objekty, které se zveřejní jako objekty modelu COM.  
  
## <a name="vbconinteroperabilitymarshalinganchor4"></a> Použití objektů modelu COM sestaveních vzájemné spolupráce  
 Téměř jako by šlo spravovaného kódu při nahrazování objekty modelu COM, které představují, používají spolupracující sestavení. Protože jde o obálkách a ne skutečné objekty modelu COM, existují však určité rozdíly mezi použitím nástrojů sestavení vzájemné spolupráce a standardní sestavení. Patří sem rozdílu vystavení tříd a datové typy parametrů a návratové hodnoty.  
  
## <a name="vbconinteroperabilitymarshalinganchor5"></a> Vystavené jako obě rozhraní třídy a třídy  
 Na rozdíl od tříd v standardní sestavení jsou přístupné třídy modelu COM ve spolupracujícím sestavení jako rozhraní a třídy, která představuje třídu COM. Název rozhraní je stejný jako u třídy modelu COM. Název třídy spolupráce je stejný jako původní třídy modelu COM, ale slovo "Třída" připojí. Předpokládejme například, že máte projekt s odkazem na sestavení vzájemné spolupráce pro objekt modelu COM. Pokud je název třídy modelu COM `MyComClass`, technologie IntelliSense a prohlížeče objektů zobrazit rozhraní s názvem `MyComClass` a třídu s názvem `MyComClassClass`.  
  
## <a name="vbconinteroperabilitymarshalinganchor6"></a> Vytvoření instance třídy rozhraní .NET Framework  
 Obecně platí, můžete vytvořit instanci [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pomocí `New` příkaz s názvem třídy. Třída modelu COM reprezentované definiční sestavení je jeden případ, ve kterém můžete použít `New` příkaz s rozhraním. Pokud použijete třídu modelu COM s `Inherits` příkazu, můžete použít rozhraní, stejně jako třídy. Následující kód ukazuje, jak vytvořit `Command` objektu v projektu, který obsahuje odkaz na objekt Microsoft ActiveX Data objekty 2.8 knihovny COM:  
  
 [!code-vb[VbVbalrInterop#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#20)]  
  
 Pokud použijete třídu modelu COM jako základ pro odvozenou třídu, však musíte použít třídu spolupráce, který představuje třídu COM, stejně jako v následujícím kódu:  
  
 [!code-vb[VbVbalrInterop#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#21)]  
  
> [!NOTE]
>  Sestavení vzájemné spolupráce implicitně implementovat rozhraní, které představují třídy modelu COM. By se neměl pokoušet použít `Implements` způsobí příkaz k implementaci těchto rozhraní nebo došlo k chybě.  
  
## <a name="vbconinteroperabilitymarshalinganchor7"></a> Datové typy parametrů a návratové hodnoty  
 Na rozdíl od členů standardní sestavení může sestavení vzájemné spolupráce členů mají datové typy, které se liší od těch, které používají v původní deklaraci objektu. I když sestavení vzájemné spolupráce implicitně převést na kompatibilní běžných typů modulu runtime jazyka typy modelu COM, měli věnovat pozornost datové typy, které jsou používány obě strany aby se zabránilo chybám za běhu. Například v modelu COM objekty vytvořené v jazyce Visual Basic verze 6.0 a starší, hodnoty typu `Integer` předpokládají [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ekvivalentní typ `Short`. Doporučuje se použít Prohlížeč objektů prozkoumat charakteristiky členů importované před jejich použitím.  
  
## <a name="vbconinteroperabilitymarshalinganchor8"></a> Modul metody na úrovni modelu COM  
 Většina objektů COM se používají tak, že vytvoříte instanci třídy pomocí modelu COM `New` – klíčové slovo a následným voláním metod objektu. Jedinou výjimkou tohoto pravidla zahrnuje objekty modelu COM, které obsahují `AppObj` nebo `GlobalMultiUse` tříd modelu COM. Takové třídy vypadat podobně jako na úrovni metod modulu ve třídách jazyka Visual Basic .NET. Visual Basic 6.0 a starší verze implicitně vytvoření instancí těchto objektů můžete při prvním volání jedné z jejich metod. Například v jazyce Visual Basic 6.0 můžete přidat odkaz na knihovnu objektů 3.6 Microsoft DAO a volání `DBEngine` metody bez vytvoření instance:  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET vyžaduje, abyste mohli používat své metody vždy vytvořit instance objektů COM. Používat tyto metody v jazyce Visual Basic, deklarovat proměnnou požadovanou třídu a použijte klíčové slovo new k přiřazení objektu k proměnné objektu. `Shared` – Klíčové slovo lze použít, když chcete Ujistěte se, že se vytvoří tento pouze jedna instance třídy.  
  
 [!code-vb[VbVbalrInterop#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#23)]  
  
## <a name="vbconinteroperabilitymarshalinganchor9"></a> Neošetřené chyby v obslužných rutinách událostí  
 Jeden běžný problém spolupráce zahrnuje chyby v obslužných rutinách událostí, které zpracovávají události vyvolané objektů COM. Tyto chyby se ignorovaly, pokud výslovně ověřujete chyby pomocí `On Error` nebo `Try...Catch...Finally` příkazy. Například následující příklad je z projektu jazyka Visual Basic .NET, který obsahuje odkaz na objekt Microsoft ActiveX Data objekty 2.8 knihovny COM.  
  
 [!code-vb[VbVbalrInterop#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#24)]  
  
 V tomto příkladu vyvolává chybu podle očekávání. Ale pokud se pokusíte stejný příklad bez `Try...Catch...Finally` bloku, chyba se ignoruje, protože, pokud jste použili `OnError Resume Next` příkazu. Bez zpracování chyb bez upozornění selže dělení nulou. Protože tyto chyby nikdy vyvolat chyby neošetřená výjimka, je důležité, abyste používali určitou formu zpracování výjimek v obslužné rutiny událostí, které zpracovávají události od objektů COM.  
  
### <a name="understanding-com-interop-errors"></a>Vysvětlení chyb vzájemné spolupráce COM  
 Bez zpracování chyb, generování spolupráce volání často chyby, které poskytují pár informací. Kdykoli je to možné, použijte strukturované zpracování vám poskytneme Další informace o problémech, které se objeví chyby. To může být zvláště užitečné při ladění aplikace. Příklad:  
  
 [!code-vb[VbVbalrInterop#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#25)]  
  
 Informace, např. popis chyby, HRESULT a příčiny chyby modelu COM. získáte zkoumání obsahu výjimek objektu.  
  
## <a name="vbconinteroperabilitymarshalinganchor10"></a> Problémy s ovládacího prvku ActiveX  
 Většina ovládacích prvků ActiveX, které využívají službu jazyka Visual Basic 6.0 fungovat bez potíže v jazyce Visual Basic .NET. Hlavní výjimky jsou ovládací prvky kontejneru nebo ovládací prvky, které vizuálně obsahují další ovládací prvky. Některé příklady starší ovládacích prvků, které nebudou správně fungovat se sadou Visual Studio jsou následující:  
  
-   Microsoft Forms 2.0 Frame – ovládací prvek  
  
-   Ovládací prvek směrem nahoru a dolů, označované také jako otočný ovládací prvek  
  
-   Ovládací prvek karty Sheridan  
  
 Existuje pouze několik řešení pro nepodporované problémy ovládacího prvku ActiveX. Pokud původní zdrojový kód vlastníte, můžete migrovat existující ovládací prvky do sady Visual Studio. V opačném případě můžete kontaktovat dodavatele softwaru aktualizovaná. NET kompatibilní s verzí ovládacích prvků k nahrazení nepodporované ovládací prvky ActiveX.  
  
## <a name="vbconinteroperabilitymarshalinganchor11"></a> Vlastnosti jen pro čtení předání ByRef ovládacích prvků  
 Visual Basic .NET někdy vyvolává chyby modelu COM jako je například "Chyba 0x800A017F CTL_E_SETNOTSUPPORTED", při předání `ReadOnly` vlastnosti některé starší ovládací prvky ActiveX jako `ByRef` parametry pro další postupy. Podobně jako volání procedur Visual Basic 6.0 nevyvolávejte chybu a parametry jsou zpracovávány jako by to předán podle hodnoty. Visual Basic .NET chybová zpráva znamená, že se pokoušíte změnit vlastnost, která nemá vlastnost `Set` postup.  
  
 Pokud máte přístup do volané procedury tuto chybu můžete zabránit pomocí `ByVal` klíčového slova pro deklarování parametrů, které přijímají `ReadOnly` vlastnosti. Příklad:  
  
 [!code-vb[VbVbalrInterop#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#26)]  
  
 Pokud nemáte přístup ke zdrojovému kódu pro procedura volána, můžete vynutit vlastnost, která má být předán podle hodnoty tak, že přidáte další sadu závorek volající procedury. Například v projektu, který obsahuje odkaz na objekt Microsoft ActiveX Data objekty 2.8 knihovny COM, můžete použít:  
  
 [!code-vb[VbVbalrInterop#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#27)]  
  
## <a name="vbconinteroperabilitymarshalinganchor12"></a> Nasazení sestavení, která zpřístupňují zprostředkovatele komunikace s objekty  
 Nasazení sestavení, které vystavit rozhraní COM prezentuje některé jedinečné výzvy. Například potenciální problém nastane, pokud samostatné aplikace odkazovat na stejné sestavení modelu COM. Tato situace je běžné při instalaci nové verze sestavení a stará verze sestavení je stále používá jiná aplikace. Pokud odinstalujete sestavení, které sdílí knihovnu DLL, můžete neúmyslně si je k dispozici pro jiná sestavení.  
  
 K tomuto problému vyhnout, by měl instalaci sdílené sestavení do globální mezipaměti sestavení (GAC) a použít MergeModule pro složku. Pokud aplikaci nejde nainstalovat v mezipaměti GAC, ho chcete nainstalovat CommonFilesFolder v podadresáři specifické pro verzi.  
  
 Sestavení, která se nesdílejí musí nacházet v adresáři s volající aplikace vedle sebe.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tlbimp.exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (exportér knihovny typů)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Návod: Implementace dědičnosti pomocí objektů COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Globální mezipaměť sestavení](../../../framework/app-domains/gac.md)
