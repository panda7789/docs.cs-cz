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
ms.openlocfilehash: 344c180cf0b9426898e17b45db768a337fd45beb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74338676"
---
# <a name="troubleshooting-interoperability-visual-basic"></a>Řešení potíží s interoperabilitou (Visual Basic)
Když pracujete s modelem COM a spravovaným kódem .NET Framework, může dojít k jednomu nebo několika následujícím běžným problémům.  
  
## <a name="vbconinteroperabilitymarshalinganchor1"></a>Zařazování spolupráce  
 V některých případech možná budete muset použít datové typy, které nejsou součástí .NET Framework. Definiční sestavení zpracovává většinu práce pro objekty modelu COM, ale může být nutné řídit datové typy, které se používají, když jsou spravované objekty vystaveny modelu COM. Například struktury knihovny tříd musí určovat `BStr` nespravovaný typ u řetězců odesílaných do objektů COM vytvořených Visual Basic 6,0 a starších verzí. V takových případech můžete použít atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute>, aby se spravované typy zobrazovaly jako nespravované typy.  
  
## <a name="vbconinteroperabilitymarshalinganchor2"></a>Export řetězců s pevnou délkou do nespravovaného kódu  
 V Visual Basic 6,0 a dřívějších verzích jsou řetězce exportovány do objektů COM jako sekvence bajtů bez ukončovacího znaku null. Pro kompatibilitu s jinými jazyky Visual Basic .NET zahrnuje ukončovací znak při exportování řetězců. Nejlepším způsobem, jak tuto nekompatibilitu vyřešit, je exportovat řetězce, které nemají znak ukončení, jako pole `Byte` nebo `Char`.  
  
## <a name="vbconinteroperabilitymarshalinganchor3"></a>Exportování hierarchií dědičnosti  
 Hierarchie spravované třídy jsou shrnuty, pokud jsou vystaveny jako objekty modelu COM. Například pokud definujete základní třídu se členem a poté zdědíte základní třídu v odvozené třídě, která je vystavena jako objekt modelu COM, klienti používající odvozenou třídu v objektu COM nebudou moci použít zděděné členy. Ke členům základní třídy lze přivodit z objektů COM pouze jako instancí základní třídy a poté pouze v případě, že je základní třída vytvořena také jako objekt modelu COM.  
  
## <a name="overloaded-methods"></a>Přetížené metody  
 I když můžete vytvořit přetížené metody pomocí Visual Basic, nejsou v modelu COM podporovány. Pokud je třída, která obsahuje přetížené metody, vystavena jako objekt modelu COM, jsou pro přetížené metody generovány nové názvy metod.  
  
 Zvažte například třídu, která má dvě přetížení metody `Synch`. Když je třída vystavena jako objekt modelu COM, mohou být nové vygenerované názvy metod `Synch` a `Synch_2`.  
  
 Přejmenování může pro uživatele objektu COM způsobit dva problémy.  
  
1. Klienti nemusí očekávat názvy generovaných metod.  
  
2. Vygenerované názvy metod ve třídě vystavené jako objekt modelu COM se mohou změnit, pokud jsou nová přetížení přidána do třídy nebo její základní třídy. To může způsobit problémy se správou verzí.  
  
 Chcete-li vyřešit oba problémy, poskytněte každému z metod jedinečný název namísto použití přetížení při vývoji objektů, které budou zveřejněny jako objekty modelu COM.  
  
## <a name="vbconinteroperabilitymarshalinganchor4"></a>Použití objektů modelu COM prostřednictvím definičních sestavení  
 Spolupracujete s sestaveními spolupráce, jako kdyby se jedná o nahrazení spravovaného kódu pro objekty modelu COM, které představují. Vzhledem k tomu, že se jedná o obálky a nikoli skutečné objekty COM, existují rozdíly mezi použitím sestavení interop a standardních sestavení. Tyto oblasti rozdílu zahrnují expozici tříd a datové typy pro parametry a návratové hodnoty.  
  
## <a name="vbconinteroperabilitymarshalinganchor5"></a>Třídy vystavené jako rozhraní a třídy  
 Na rozdíl od tříd ve standardních sestaveních jsou třídy COM vystaveny v sestaveních spolupráce jako rozhraní a třída, která představuje třídu modelu COM. Název rozhraní je stejný jako třída modelu COM. Název třídy interoperability je stejný jako původní třída COM, ale je připojená slova "Class". Předpokládejme například, že máte projekt s odkazem na definiční sestavení pro objekt modelu COM. Pokud je třída COM pojmenována `MyComClass`, IntelliSense a Prohlížeč objektů zobrazit rozhraní s názvem `MyComClass` a třídu s názvem `MyComClassClass`.  
  
## <a name="vbconinteroperabilitymarshalinganchor6"></a>Vytváření instancí třídy .NET Framework  
 Obecně se vytvoří instance .NET Framework třídy pomocí příkazu `New` s názvem třídy. Pokud je třída modelu COM reprezentovaná definičním sestavením, jedná se o jeden případ, ve kterém můžete použít příkaz `New` s rozhraním. Pokud nepoužíváte třídu COM s příkazem `Inherits`, lze rozhraní použít stejně jako třídu. Následující kód ukazuje, jak vytvořit objekt `Command` v projektu, který má odkaz na objekt COM knihovny Microsoft rozhraní ADO (ActiveX Data Objects) 2,8:  
  
 [!code-vb[VbVbalrInterop#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#20)]  
  
 Pokud však používáte třídu COM jako základ pro odvozenou třídu, je nutné použít třídu interoperability, která představuje třídu modelu COM, jak je uvedeno v následujícím kódu:  
  
 [!code-vb[VbVbalrInterop#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#21)]  
  
> [!NOTE]
> Sestavení vzájemné spolupráce implicitně implementují rozhraní, která reprezentují třídy COM. Neměli byste se pokoušet použít příkaz `Implements` k implementaci těchto rozhraní nebo výsledkem dojde k chybě.  
  
## <a name="vbconinteroperabilitymarshalinganchor7"></a>Datové typy pro parametry a návratové hodnoty  
 Na rozdíl od členů standardních sestavení mohou členové definičního sestavení mít datové typy, které se liší od těch, které jsou použity v původní deklaraci objektu. I když definiční sestavení implicitně převádějí typy modelu COM na kompatibilní typy modulu CLR (Common Language Runtime), měli byste věnovat pozornost datovým typům, které jsou používány oběma stranami, a zabránit tak chybám za běhu. Například v objektech COM vytvořených v Visual Basic 6,0 a starších verzích mají hodnoty typu `Integer` předpokládat .NET Framework ekvivalentní typ `Short`. Doporučuje se použít Prohlížeč objektů k prohlédnutí charakteristiky importovaných členů před jejich použitím.  
  
## <a name="vbconinteroperabilitymarshalinganchor8"></a>Metody modulu COM na úrovni modulů  
 Většina objektů COM je používána vytvořením instance třídy COM pomocí klíčového slova `New` a následným voláním metod objektu. Jedinou výjimkou z tohoto pravidla jsou objekty COM, které obsahují `AppObj` nebo `GlobalMultiUse` třídy COM. Takové třídy se podobají metodám na úrovni modulu v Visual Basic třídy .NET. Visual Basic 6,0 a starší verze implicitně vytvářejí instance těchto objektů, při prvním volání jedné z jejich metod. Například v Visual Basic 6,0 můžete přidat odkaz na knihovnu objektů Microsoft DAO 3,6 a volat metodu `DBEngine` bez prvotního vytvoření instance:  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET vyžaduje, abyste vždy vytvořili instance objektů COM předtím, než budete moci použít jejich metody. Chcete-li použít tyto metody v Visual Basic, deklarujte proměnnou požadované třídy a použijte klíčové slovo New k přiřazení objektu proměnné objektu. Klíčové slovo `Shared` lze použít, pokud chcete zajistit, aby byla vytvořena pouze jedna instance třídy.  
  
 [!code-vb[VbVbalrInterop#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#23)]  
  
## <a name="vbconinteroperabilitymarshalinganchor9"></a>Neošetřené chyby v obslužných rutinách událostí  
 Mezi běžné problémy s interoperabilitou patří chyby obslužných rutin událostí, které zpracovávají události vyvolané objekty COM. Takové chyby jsou ignorovány, pokud nezjistíte chyby pomocí příkazů `On Error` nebo `Try...Catch...Finally`. Například následující příklad je z projektu Visual Basic .NET, který má odkaz na objekt COM knihovny Microsoft rozhraní ADO (ActiveX Data Objects) 2,8.  
  
 [!code-vb[VbVbalrInterop#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#24)]  
  
 Tento příklad vyvolává chybu podle očekávání. Nicméně pokud se pokusíte použít stejný příklad bez blokování `Try...Catch...Finally`, je Chyba ignorována, jako kdybyste použili příkaz `OnError Resume Next`. Bez zpracování chyb se dělení nulou nezdařilo. Vzhledem k tomu, že tyto chyby nikdy nevyvolávají chyby neošetřené výjimky, je důležité použít určitou formu zpracování výjimek v obslužných rutinách událostí, které zpracovávají události z objektů COM.  
  
### <a name="understanding-com-interop-errors"></a>Porozumění chybám komunikace s objekty COM  
 Bez zpracování chyb se v volání spolupráce často generují chyby, které poskytují málo informací. Kdykoli je to možné, použijte strukturované zpracování chyb k poskytnutí dalších informací o problémech, když k nim dojde. To může být obzvláště užitečné při ladění aplikací. Příklad:  
  
 [!code-vb[VbVbalrInterop#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#25)]  
  
 Můžete najít informace, jako je popis chyby, HRESULT a zdroj chyb COM, prozkoumáním obsahu objektu výjimky.  
  
## <a name="vbconinteroperabilitymarshalinganchor10"></a>Problémy s ovládacím prvkem ActiveX  
 Většina ovládacích prvků ActiveX, které pracují s Visual Basic 6,0, pracuje s Visual Basic .NET bez problémů. Hlavní výjimky jsou ovládací prvky kontejneru nebo ovládací prvky, které vizuálně obsahují jiné ovládací prvky. Některé příklady starších ovládacích prvků, které nefungují správně se sadou Visual Studio, jsou následující:  
  
- Microsoft Forms 2,0 – ovládací prvek rámce  
  
- Ovládací prvek rozevíracího seznamu, označovaný také jako otočný ovládací prvek  
  
- Ovládací prvek karta Sheridan  
  
 Pro nepodporované problémy s ovládacími prvky ActiveX existuje pouze několik alternativních řešení. Existující ovládací prvky můžete migrovat do sady Visual Studio, pokud vlastníte původní zdrojový kód. V opačném případě můžete zkontrolovat, jestli se dodavatelé softwaru aktualizovaly. Verze ovládacích prvků, které jsou kompatibilní s NET, aby nahradily nepodporované ovládací prvky ActiveX.  
  
## <a name="vbconinteroperabilitymarshalinganchor11"></a>Předávání vlastností jen pro čtení u ovládacích prvků ByRef  
 Visual Basic rozhraní .NET někdy vyvolá chyby modelu COM, jako je "Error 0x800A017F CTL_E_SETNOTSUPPORTED", při předání `ReadOnly` vlastností některých starších ovládacích prvků ActiveX jako `ByRef` parametrů jiným postupům. Podobná volání procedur z Visual Basic 6,0 nevyvolávají chybu a parametry se považují za, pokud jste je předali podle hodnoty. Chybová zpráva Visual Basic .NET označuje, že se pokoušíte změnit vlastnost, která neobsahuje vlastnost `Set` proceduru.  
  
 Máte-li přístup k proceduře, která je volána, můžete tuto chybu zabránit pomocí klíčového slova `ByVal` k deklaraci parametrů, které přijmou vlastnosti `ReadOnly`. Příklad:  
  
 [!code-vb[VbVbalrInterop#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#26)]  
  
 Pokud nemáte přístup ke zdrojovému kódu pro volání procedury, můžete vynutit, aby vlastnost byla předána hodnotou přidáním nadbytečné sady hranatých závorek kolem volajícího postupu. Například v projektu, který má odkaz na objekt COM knihovny Microsoft rozhraní ADO (ActiveX Data Objects) 2,8, můžete použít:  
  
 [!code-vb[VbVbalrInterop#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#27)]  
  
## <a name="vbconinteroperabilitymarshalinganchor12"></a>Nasazení sestavení, která zveřejňují spolupráci  
 Nasazení sestavení, která zveřejňují rozhraní modelu COM, představují některé jedinečné výzvy. Například potenciální problém nastane, pokud samostatné aplikace odkazují na stejné sestavení COM. Tato situace je obvyklá, pokud je nainstalována nová verze sestavení a jiná aplikace stále používá starou verzi sestavení. Pokud odinstalujete sestavení, které sdílí knihovnu DLL, můžete ji neúmyslně znepřístupnit pro ostatní sestavení.  
  
 Chcete-li se tomuto problému vyhnout, měli byste nainstalovat sdílená sestavení do globální mezipaměti sestavení (GAC) a použít pro komponentu MergeModule. Pokud nemůžete nainstalovat aplikaci do mezipaměti GAC, měla by být nainstalována do CommonFilesFolder v podadresáři specifické pro danou verzi.  
  
 Sestavení, která nejsou sdílena, by měla být umístěná vedle sebe v adresáři pomocí volající aplikace.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tlbimp.exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (exportér knihovny typů)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Návod: Implementace dědičnosti pomocí objektů COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Globální mezipaměť sestavení](../../../framework/app-domains/gac.md)
