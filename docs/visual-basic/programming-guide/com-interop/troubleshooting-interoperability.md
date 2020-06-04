---
title: Řešení potíží s interoperabilitou
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
ms.openlocfilehash: 0890bac80396feaf37d4ba917c1e3fafb8579981
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396763"
---
# <a name="troubleshooting-interoperability-visual-basic"></a>Řešení potíží s interoperabilitou (Visual Basic)
Když pracujete s modelem COM a spravovaným kódem .NET Framework, může dojít k jednomu nebo několika následujícím běžným problémům.  
  
## <a name="interop-marshaling"></a><a name="vbconinteroperabilitymarshalinganchor1"></a>Zařazování spolupráce  
 V některých případech možná budete muset použít datové typy, které nejsou součástí .NET Framework. Definiční sestavení zpracovává většinu práce pro objekty modelu COM, ale může být nutné řídit datové typy, které se používají, když jsou spravované objekty vystaveny modelu COM. Například struktury knihovny tříd musí určovat `BStr` nespravovaný typ u řetězců odesílaných do objektů COM vytvořených pomocí Visual Basic 6,0 a starších verzí. V takových případech můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut, který způsobí, že spravované typy budou vystaveny jako nespravované typy.  
  
## <a name="exporting-fixed-length-strings-to-unmanaged-code"></a><a name="vbconinteroperabilitymarshalinganchor2"></a>Export řetězců s pevnou délkou do nespravovaného kódu  
 V Visual Basic 6,0 a dřívějších verzích jsou řetězce exportovány do objektů COM jako sekvence bajtů bez ukončovacího znaku null. Pro kompatibilitu s jinými jazyky Visual Basic .NET zahrnuje ukončovací znak při exportování řetězců. Nejlepším způsobem, jak tuto nekompatibilitu vyřešit, je exportovat řetězce, které chybí znak ukončení jako pole `Byte` nebo `Char` .  
  
## <a name="exporting-inheritance-hierarchies"></a><a name="vbconinteroperabilitymarshalinganchor3"></a>Exportování hierarchií dědičnosti  
 Hierarchie spravované třídy jsou shrnuty, pokud jsou vystaveny jako objekty modelu COM. Například pokud definujete základní třídu se členem a poté zdědíte základní třídu v odvozené třídě, která je vystavena jako objekt modelu COM, klienti používající odvozenou třídu v objektu COM nebudou moci použít zděděné členy. Ke členům základní třídy lze přivodit z objektů COM pouze jako instancí základní třídy a poté pouze v případě, že je základní třída vytvořena také jako objekt modelu COM.  
  
## <a name="overloaded-methods"></a>Přetížené metody  
 I když můžete vytvořit přetížené metody pomocí Visual Basic, nejsou v modelu COM podporovány. Pokud je třída, která obsahuje přetížené metody, vystavena jako objekt modelu COM, jsou pro přetížené metody generovány nové názvy metod.  
  
 Zvažte například třídu, která má dvě přetížení `Synch` metody. Když je třída vystavena jako objekt modelu COM, mohou být nově vygenerované názvy metody `Synch` a `Synch_2` .  
  
 Přejmenování může pro uživatele objektu COM způsobit dva problémy.  
  
1. Klienti nemusí očekávat názvy generovaných metod.  
  
2. Vygenerované názvy metod ve třídě vystavené jako objekt modelu COM se mohou změnit, pokud jsou nová přetížení přidána do třídy nebo její základní třídy. To může způsobit problémy se správou verzí.  
  
 Chcete-li vyřešit oba problémy, poskytněte každému z metod jedinečný název namísto použití přetížení při vývoji objektů, které budou zveřejněny jako objekty modelu COM.  
  
## <a name="use-of-com-objects-through-interop-assemblies"></a><a name="vbconinteroperabilitymarshalinganchor4"></a>Použití objektů modelu COM prostřednictvím definičních sestavení  
 Spolupracujete s sestaveními spolupráce, jako kdyby se jedná o nahrazení spravovaného kódu pro objekty modelu COM, které představují. Vzhledem k tomu, že se jedná o obálky a nikoli skutečné objekty COM, existují rozdíly mezi použitím sestavení interop a standardních sestavení. Tyto oblasti rozdílu zahrnují expozici tříd a datové typy pro parametry a návratové hodnoty.  
  
## <a name="classes-exposed-as-both-interfaces-and-classes"></a><a name="vbconinteroperabilitymarshalinganchor5"></a>Třídy vystavené jako rozhraní a třídy  
 Na rozdíl od tříd ve standardních sestaveních jsou třídy COM vystaveny v sestaveních spolupráce jako rozhraní a třída, která představuje třídu modelu COM. Název rozhraní je stejný jako třída modelu COM. Název třídy interoperability je stejný jako původní třída COM, ale je připojená slova "Class". Předpokládejme například, že máte projekt s odkazem na definiční sestavení pro objekt modelu COM. Pokud je třída COM pojmenována `MyComClass` , technologie IntelliSense a prohlížeč objektů zobrazí rozhraní s názvem `MyComClass` a třídu s názvem `MyComClassClass` .  
  
## <a name="creating-instances-of-a-net-framework-class"></a><a name="vbconinteroperabilitymarshalinganchor6"></a>Vytváření instancí třídy .NET Framework  
 Obecně se vytvoří instance .NET Framework třídy pomocí `New` příkazu s názvem třídy. Pokud je třída modelu COM reprezentovaná definičním sestavením, jedná se o jeden případ, ve kterém můžete použít `New` příkaz s rozhraním. Pokud nepoužíváte třídu COM s `Inherits` příkazem, můžete použít rozhraní stejně jako třídu. Následující kód ukazuje, jak vytvořit `Command` objekt v projektu, který má odkaz na objekt COM knihovny Microsoft rozhraní ADO (ActiveX Data Objects) 2,8:  
  
 [!code-vb[VbVbalrInterop#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#20)]  
  
 Pokud však používáte třídu COM jako základ pro odvozenou třídu, je nutné použít třídu interoperability, která představuje třídu modelu COM, jak je uvedeno v následujícím kódu:  
  
 [!code-vb[VbVbalrInterop#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#21)]  
  
> [!NOTE]
> Sestavení vzájemné spolupráce implicitně implementují rozhraní, která reprezentují třídy COM. Neměli byste se pokoušet použít `Implements` příkaz k implementaci těchto rozhraní nebo výsledkem bude chyba.  
  
## <a name="data-types-for-parameters-and-return-values"></a><a name="vbconinteroperabilitymarshalinganchor7"></a>Datové typy pro parametry a návratové hodnoty  
 Na rozdíl od členů standardních sestavení mohou členové definičního sestavení mít datové typy, které se liší od těch, které jsou použity v původní deklaraci objektu. I když definiční sestavení implicitně převádějí typy modelu COM na kompatibilní typy modulu CLR (Common Language Runtime), měli byste věnovat pozornost datovým typům, které jsou používány oběma stranami, a zabránit tak chybám za běhu. Například v objektech COM vytvořených v Visual Basic 6,0 a starších verzích hodnoty typu `Integer` předpokládají .NET Framework ekvivalentní typ, `Short` . Doporučuje se použít Prohlížeč objektů k prohlédnutí charakteristiky importovaných členů před jejich použitím.  
  
## <a name="module-level-com-methods"></a><a name="vbconinteroperabilitymarshalinganchor8"></a>Metody modulu COM na úrovni modulů  
 Většina objektů COM je používána vytvořením instance třídy COM pomocí `New` klíčového slova a následným voláním metod objektu. Jedinou výjimkou z tohoto pravidla jsou objekty COM, které obsahují `AppObj` nebo `GlobalMultiUse` třídy com. Takové třídy se podobají metodám na úrovni modulu v Visual Basic třídy .NET. Visual Basic 6,0 a starší verze implicitně vytvářejí instance těchto objektů, při prvním volání jedné z jejich metod. Například v Visual Basic 6,0 můžete přidat odkaz na knihovnu objektů Microsoft DAO 3,6 a volat `DBEngine` metodu bez prvotního vytvoření instance:  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET vyžaduje, abyste vždy vytvořili instance objektů COM předtím, než budete moci použít jejich metody. Chcete-li použít tyto metody v Visual Basic, deklarujte proměnnou požadované třídy a použijte klíčové slovo New k přiřazení objektu proměnné objektu. `Shared`Klíčové slovo lze použít, pokud chcete zajistit, aby byla vytvořena pouze jedna instance třídy.  
  
 [!code-vb[VbVbalrInterop#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#23)]  
  
## <a name="unhandled-errors-in-event-handlers"></a><a name="vbconinteroperabilitymarshalinganchor9"></a>Neošetřené chyby v obslužných rutinách událostí  
 Mezi běžné problémy s interoperabilitou patří chyby obslužných rutin událostí, které zpracovávají události vyvolané objekty COM. Takové chyby jsou ignorovány, pokud nezjistíte chyby `On Error` pomocí `Try...Catch...Finally` příkazů nebo. Například následující příklad je z projektu Visual Basic .NET, který má odkaz na objekt COM knihovny Microsoft rozhraní ADO (ActiveX Data Objects) 2,8.  
  
 [!code-vb[VbVbalrInterop#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#24)]  
  
 Tento příklad vyvolává chybu podle očekávání. Nicméně pokud se pokusíte použít stejný příklad bez `Try...Catch...Finally` bloku, je Chyba ignorována, jako kdybyste použili `OnError Resume Next` příkaz. Bez zpracování chyb se dělení nulou nezdařilo. Vzhledem k tomu, že tyto chyby nikdy nevyvolávají chyby neošetřené výjimky, je důležité použít určitou formu zpracování výjimek v obslužných rutinách událostí, které zpracovávají události z objektů COM.  
  
### <a name="understanding-com-interop-errors"></a>Porozumění chybám komunikace s objekty COM  
 Bez zpracování chyb se v volání spolupráce často generují chyby, které poskytují málo informací. Kdykoli je to možné, použijte strukturované zpracování chyb k poskytnutí dalších informací o problémech, když k nim dojde. To může být obzvláště užitečné při ladění aplikací. Příklad:  
  
 [!code-vb[VbVbalrInterop#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#25)]  
  
 Můžete najít informace, jako je popis chyby, HRESULT a zdroj chyb COM, prozkoumáním obsahu objektu výjimky.  
  
## <a name="activex-control-issues"></a><a name="vbconinteroperabilitymarshalinganchor10"></a>Problémy s ovládacím prvkem ActiveX  
 Většina ovládacích prvků ActiveX, které pracují s Visual Basic 6,0, pracuje s Visual Basic .NET bez problémů. Hlavní výjimky jsou ovládací prvky kontejneru nebo ovládací prvky, které vizuálně obsahují jiné ovládací prvky. Některé příklady starších ovládacích prvků, které nefungují správně se sadou Visual Studio, jsou následující:  
  
- Microsoft Forms 2,0 – ovládací prvek rámce  
  
- Ovládací prvek rozevíracího seznamu, označovaný také jako otočný ovládací prvek  
  
- Ovládací prvek karta Sheridan  
  
 Pro nepodporované problémy s ovládacími prvky ActiveX existuje pouze několik alternativních řešení. Existující ovládací prvky můžete migrovat do sady Visual Studio, pokud vlastníte původní zdrojový kód. V opačném případě můžete zkontrolovat, jestli se dodavatelé softwaru aktualizovaly. Verze ovládacích prvků, které jsou kompatibilní s NET, aby nahradily nepodporované ovládací prvky ActiveX.  
  
## <a name="passing-readonly-properties-of-controls-byref"></a><a name="vbconinteroperabilitymarshalinganchor11"></a>Předávání vlastností jen pro čtení u ovládacích prvků ByRef  
 Visual Basic .NET někdy vyvolá chyby modelu COM, například "Error 0x800A017F CTL_E_SETNOTSUPPORTED", při předání `ReadOnly` vlastností některých starších ovládacích prvků ActiveX jako `ByRef` parametrů jiným postupům. Podobná volání procedur z Visual Basic 6,0 nevyvolávají chybu a parametry se považují za, pokud jste je předali podle hodnoty. Chybová zpráva Visual Basic .NET označuje, že se pokoušíte změnit vlastnost, která nemá `Set` proceduru vlastnosti.  
  
 Máte-li přístup k proceduře, která je volána, můžete tuto chybu zabránit pomocí `ByVal` klíčového slova k deklaraci parametrů, které přijímají `ReadOnly` Vlastnosti. Příklad:  
  
 [!code-vb[VbVbalrInterop#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#26)]  
  
 Pokud nemáte přístup ke zdrojovému kódu pro volání procedury, můžete vynutit, aby vlastnost byla předána hodnotou přidáním nadbytečné sady hranatých závorek kolem volajícího postupu. Například v projektu, který má odkaz na objekt COM knihovny Microsoft rozhraní ADO (ActiveX Data Objects) 2,8, můžete použít:  
  
 [!code-vb[VbVbalrInterop#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#27)]  
  
## <a name="deploying-assemblies-that-expose-interop"></a><a name="vbconinteroperabilitymarshalinganchor12"></a>Nasazení sestavení, která zveřejňují spolupráci  
 Nasazení sestavení, která zveřejňují rozhraní modelu COM, představují některé jedinečné výzvy. Například potenciální problém nastane, pokud samostatné aplikace odkazují na stejné sestavení COM. Tato situace je obvyklá, pokud je nainstalována nová verze sestavení a jiná aplikace stále používá starou verzi sestavení. Pokud odinstalujete sestavení, které sdílí knihovnu DLL, můžete ji neúmyslně znepřístupnit pro ostatní sestavení.  
  
 Chcete-li se tomuto problému vyhnout, měli byste nainstalovat sdílená sestavení do globální mezipaměti sestavení (GAC) a použít pro komponentu MergeModule. Pokud nemůžete nainstalovat aplikaci do mezipaměti GAC, měla by být nainstalována do CommonFilesFolder v podadresáři specifické pro danou verzi.  
  
 Sestavení, která nejsou sdílena, by měla být umístěná vedle sebe v adresáři pomocí volající aplikace.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Zprostředkovatel komunikace s objekty COM](index.md)
- [Tlbimp. exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp. exe (Exportér knihovny typů)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Návod: Implementace dědičnosti pomocí objektů COM](walkthrough-implementing-inheritance-with-com-objects.md)
- [Inherits – příkaz](../../language-reference/statements/inherits-statement.md)
- [Globální mezipaměť sestavení](../../../framework/app-domains/gac.md)
