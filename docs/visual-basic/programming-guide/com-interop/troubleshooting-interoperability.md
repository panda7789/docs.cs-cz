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
ms.openlocfilehash: 65005dbbe42f52b3159c8e595972dace3064f986
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-interoperability-visual-basic"></a>Řešení potíží s interoperabilitou (Visual Basic)
Když jste vzájemnou spolupráci mezi COM a spravovaného kódu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], můžete narazit na jeden nebo více z následujících běžných problémů.  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a> Zařazování spolupráce  
 V některých případech možná budete muset použít datové typy, které nejsou součástí [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Sestavení spolupráce zpracovávat většinu práce pro objekty modelu COM, ale možná budete muset řídit typy dat, které se používají při spravované objekty jsou viditelné na modelu COM. Například musíte zadat struktury v knihovny tříd `BStr` nespravované typ řetězce posílá COM – objekty vytvořené Visual Basic 6.0 a starší verze. V takových případech můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributu způsobí spravovaných typů, jako nespravované typy.  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a> Export řetězce pevné délky na nespravovaný kód  
 V jazyce Visual Basic 6.0 a starší verze řetězce exportují se objekty modelu COM jako pořadí bajtů bez null ukončení znaků. Pro kompatibilitu s jinými jazyky Visual Basic .NET obsahuje znak ukončení při exportu řetězce. Nejlepší způsob, jak vyřešit tuto nekompatibilitu se neexportují řetězce, které chybí ukončovací znak jako pole `Byte` nebo `Char`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a> Export hierarchie dědičnosti  
 Spravované třídy, které hierarchií do jedné se při zveřejněné jako objekty modelu COM. Například pokud definice základní třídy, se členem a pak dědění základní třídy odvozené třídy, který je zveřejněný jako objekt COM, klienti, kteří používají odvozené třídy v objektu COM nebudou moci používat zděděné členy. Členy základní třídy lze přistupovat z COM – objekty pouze jako instance základní třídy a potom pouze v případě, že základní třídy je taky vytvořit jako objekt COM.  
  
## <a name="overloaded-methods"></a>Přetížené metody  
 I když přetížené metody můžete vytvořit pomocí jazyka Visual Basic, nejsou podporovány COM. Pokud třídu, která obsahuje přetížené metody, které je vystavený jako objekt COM, nové názvy metoda jsou generovány pro přetížené metody.  
  
 Představte si třeba třídy, která má dvě přetížení `Synch` metoda. Pokud třída je vystavený jako objekt COM, může být nové názvy generované metoda `Synch` a `Synch_2`.  
  
 Přejmenováním může způsobit problémy dva pro spotřebitele objektu COM.  
  
1.  Klienti nemusí očekávají, že názvy generované metoda.  
  
2.  Názvy generované metod ve třídě jako objekty modelu COM lze změnit, pokud nové přetížení se přidají do třídy nebo její základní třída. To může způsobit problémy se správou verzí.  
  
 Obě problémy vyřešíte poskytněte každá metoda jedinečný název, místo použití přetížení, když vyvíjíte objekty, které jsou k dispozici jako objekty modelu COM.  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a> Použití objektů COM spolupráce – sestavení  
 Téměř jako by šlo náhrady spravovaného kódu pro objekty modelu COM, které reprezentují použijete spolupráce – sestavení. Protože jsou obálky a ne skutečné objekty modelu COM, existují však určité rozdíly mezi použitím sestavení vzájemné spolupráce a standardní sestavení. Rozdíl v těchto oblastech zahrnují ohrožení tříd a typů dat pro parametry a návratové hodnoty.  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a> Třídy, které jsou zveřejněné jako obě rozhraní a třídy  
 Na rozdíl od třídy v standardní sestavení COM třídy jsou přístupné spolupráce – sestavení jako třída, která představuje třídy COM i rozhraní. Název rozhraní je stejná jako třídy COM. Název třídy spolupráce je stejný jako u původního třídy COM, ale slovem "Třída" připojí. Předpokládejme například, že máte projekt se odkaz na sestavení vzájemné spolupráce pro objekt COM. Pokud je název třídy COM `MyComClass`, IntelliSense a prohlížeč objektů zobrazit rozhraní s názvem `MyComClass` a třídy s názvem `MyComClassClass`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a> Vytváření instancí třídy rozhraní .NET Framework  
 Obecně platí, vytvořte instanci [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pomocí `New` příkaz s název třídy. Třída COM reprezentované spolupráce sestavení je jeden případ, kdy můžete použít `New` příkaz s rozhraní. Pokud používáte třídy COM s `Inherits` prohlášení, můžete použít rozhraní, stejně jako třídu. Následující kód ukazuje, jak vytvořit `Command` objekt v projektu, který obsahuje odkaz na objekt Microsoft ActiveX Data objekty 2.8 knihovny COM:  
  
 [!code-vb[VbVbalrInterop#20](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_1.vb)]  
  
 Pokud používáte jako základní třídy COM odvozené třídy, ale musíte použít spolupráce třídu, která představuje třídy COM, jako v následujícím kódu:  
  
 [!code-vb[VbVbalrInterop#21](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_2.vb)]  
  
> [!NOTE]
>  Sestavení spolupráce implicitně implementovat rozhraní, které představují třídy COM. By se neměl pokoušet použít `Implements` způsobí příkaz k implementaci těchto rozhraní nebo došlo k chybě.  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a> Datové typy pro parametry a návratové hodnoty  
 Na rozdíl od členů standardní sestavení může mít členy sestavení vzájemné spolupráce datové typy, které se liší od těch, které používá v původní deklarace objektu. I když sestavení vzájemné spolupráce implicitně převést na kompatibilní běžné typy runtime jazyka typy modelu COM, měli byste věnovat pozornost do datových typů, které jsou používány na obou stranách aby se zabránilo chybám za běhu. Například v modelu COM objekty vytvořené v jazyce Visual Basic 6.0 a starší verze, hodnoty typu `Integer` předpokládá [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ekvivalentní typu `Short`. Doporučuje se použít Prohlížeč objektů pro zjištění vlastností importované členů dříve, než je použijete.  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a> Modul metody na úrovni modelu COM  
 Většinu objektů COM používají vytvoření instance třídy modelu COM pomocí `New` – klíčové slovo a pak volání metody objektu. Jedinou výjimkou tohoto pravidla zahrnuje objekty modelu COM, které obsahují `AppObj` nebo `GlobalMultiUse` třídy COM. Těchto tříd podobat modulu úrovně metody v jazyce Visual Basic .NET třídy. Visual Basic 6.0 a starší verze implicitně instancí těchto objektů za vás vytvořit při prvním volání jednoho z své metody. Ve Visual Basic 6.0 můžete například přidat odkaz na knihovnu Microsoft DAO 3.6 objektu a volání `DBEngine` metoda bez vytvoření první instance:  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET vyžaduje, abyste mohli používat své metody vždy vytváření instancí objektů COM. Chcete-li používat tyto metody v jazyce Visual Basic, deklarovat proměnnou požadovanou třídu a použijte new – klíčové slovo přiřazení objektu k proměnné objektu. `Shared` – Klíčové slovo lze použít, pokud chcete zajistit, že pouze jedna instance třídy se vytvoří.  
  
 [!code-vb[VbVbalrInterop#23](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_3.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a> Neošetřené chyby v obslužné rutiny událostí  
 Jedním z běžných problémů spolupráce zahrnuje chyby v obslužné rutiny, které zpracovávají události vyvolané COM – objekty. Takové chyby se ignoruje, pokud je konkrétně zkontrolovat chyby pomocí `On Error` nebo `Try...Catch...Finally` příkazy. Například v následujícím příkladu je z projektu Visual Basic .NET, který obsahuje odkaz na objekt Microsoft ActiveX Data objekty 2.8 knihovny COM.  
  
 [!code-vb[VbVbalrInterop#24](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_4.vb)]  
  
 Tento příklad vyvolá chybu podle očekávání. Ale pokud se pokusíte příkladě bez `Try...Catch...Finally` bloku k chybě se ignoruje, protože pokud jste použili `OnError Resume Next` příkaz. Bez zpracování chyb bez upozornění selže dělení nulou. Protože takové chyby nikdy vyvolání chyby neošetřených výjimek, je důležité, abyste používali určitou formu zpracování výjimek v obslužné rutiny událostí, které zpracovávají události z COM – objekty.  
  
### <a name="understanding-com-interop-errors"></a>Principy chyb zprostředkovatele komunikace s objekty COM  
 Spolupráce volání generovat bez zpracování chyb, často chyby, které obsahují malé informace. Pokud je to možné, použijte strukturované zpracování poskytnout další informace o problémech při jejich výskytu chyb. To může být obzvláště užitečné při ladění aplikace. Příklad:  
  
 [!code-vb[VbVbalrInterop#25](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_5.vb)]  
  
 Informace, jako je popis chyby, HRESULT a zdroj COM chyby můžete najít tak, že prověří obsah objekt výjimky.  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a> Ovládací prvek ActiveX problémy  
 Většina ovládacích prvků ActiveX, které pracují s Visual Basic 6.0 Visual Basic .NET pracovat bez řešení problémů. Hlavní výjimky jsou ovládací prvky kontejneru nebo ovládací prvky, které vizuálně obsahují další ovládací prvky. Některé příklady starší ovládacích prvků, které nefungují správně pomocí sady Visual Studio jsou následující:  
  
-   Ovládací prvek Microsoft Forms 2.0 rámce  
  
-   Číselník – ovládací prvek, také známé jako ovládací prvek typu číselník  
  
-   Ovládací prvek karty Sheridan  
  
 Existují jenom několik řešení pro nepodporovaný problémy ovládací prvek ActiveX. Visual Studio můžete migrovat stávající ovládací prvky, pokud jste vlastníkem původní zdrojový kód. Jinak můžete zkontrolovat s dodavateli softwaru pro aktualizovat. NET kompatibilní s verzí ovládacích prvků k nahrazení nepodporované ovládací prvky ActiveX.  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a> Vlastnosti jen pro čtení předávání ByRef ovládací prvky  
 Visual Basic .NET někdy vyvolá chyby COM, jako je například "Chyba 0x800A017F CTL_E_SETNOTSUPPORTED", při předání `ReadOnly` vlastnosti některé starší ovládací prvky ActiveX jako `ByRef` parametry pro další postupy. Podobně jako u volání procedur jazyka Visual Basic 6.0 není vyvolá chybu, a parametry jsou zpracovány jako v případě, že jste je předaná hodnota. Visual Basic .NET chybová zpráva znamená, že se pokoušíte změnit vlastnost, která nemá vlastnost `Set` postupu.  
  
 Pokud máte přístup k procedura volaná, abyste zabránili této chyby pomocí `ByVal` – klíčové slovo deklarovat parametry, které přijímají `ReadOnly` vlastnosti. Příklad:  
  
 [!code-vb[VbVbalrInterop#26](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_6.vb)]  
  
 Pokud nemáte přístup ke zdrojovému kódu pro proceduru volané, můžete vynutit vlastnost, která má být předaná hodnota přidáním další sadu hranaté závorky kolem volání procedury. Například v projektu, který obsahuje odkaz na objekt Microsoft ActiveX Data objekty 2.8 knihovny COM, můžete použít:  
  
 [!code-vb[VbVbalrInterop#27](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_7.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a> Nasazení sestavení, které zveřejňují zprostředkovatel komunikace s objekty  
 Nasazení sestavení, které zveřejňují rozhraní modelu COM uvede některé jedinečné výzvy. Například na potenciální problém nastane, když do stejného sestavení modelu COM odkazovat na samostatné aplikace. Tato situace je běžné při instalaci nové verze sestavení a stará verze sestavení je stále používá jiná aplikace. Pokud odinstalujete sestavení, které sdílí knihovnu DLL, lze neúmyslně znepřístupnit ho na jiné sestavení.  
  
 K tomuto problému nedošlo, musíte nainstalovat sdílená sestavení do globální mezipaměti sestavení (GAC) a použít MergeModule pro komponentu. Pokud v mezipaměti GAC nemůžete instalovat aplikace, je třeba nainstalovat do CommonFilesFolder v podadresáři specifické pro verzi.  
  
 Sestavení, které nejsou sdílené musí nacházet v adresáři s volající aplikace vedle sebe.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (exportér knihovny typů)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Návod: Implementace dědičnosti pomocí objektů COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Globální mezipaměť sestavení](../../../framework/app-domains/gac.md)
