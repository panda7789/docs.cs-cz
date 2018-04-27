---
title: 'Návod: Volání rozhraní API systému Windows (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls [Visual Basic], walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement [Visual Basic], declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 34bfb732e2d99b259811573a427ae66628c7fc3a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>Návod: Volání rozhraní API systému Windows (Visual Basic)
Rozhraní API systému Windows jsou dynamické knihovny (DLL), které jsou součástí operačního systému Windows. Můžete použít je k provádění úloh, když je k zápisu ekvivalentní postupy. Například systém Windows nabízí funkce s názvem `FlashWindowEx` , umožňuje provádět alternativní mezi světlým a tmavým odstínech záhlaví pro aplikaci.  
  
 Výhodou použití rozhraní API systému Windows ve vašem kódu je v okamžiku vývoje si mohou uložit, protože obsahují desítek užitečné funkce, které jsou již zapsány a čekání, který se má použít. Nevýhodou je, že rozhraní API systému Windows může být složité fungovat s a nepřijímá, když dojde k potížím.  
  
 Rozhraní API systému Windows představují zvláštní kategorii interoperability. Rozhraní API systému Windows nepoužívejte spravovaného kódu, nemají předdefinované knihovny typů a použít datové typy, které se liší od těch, které používá pomocí sady Visual Studio. Z důvodu těchto rozdílů a protože rozhraní API systému Windows nejsou objekty modelu COM, interoperabilita s rozhraní API systému Windows a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] se provádí pomocí platformy vyvolání, nebo PInvoke. Vyvolání platformy je služba, což umožňuje spravovat kódu volání nespravovaných funkcí, které jsou implementované v knihovnách DLL. Další informace najdete v tématu [využívání nespravovaných funkcí DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md). Můžete použít PInvoke v jazyce Visual Basic pomocí `Declare` příkaz nebo použití `DllImport` atribut procedury.  
  
 Volání rozhraní API systému Windows byly důležitou součástí jazyka Visual Basic programování v minulosti, ale jsou zřídka nezbytné s Visual Basic .NET. Pokud je to možné, používejte spravovaného kódu z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] k provádění úloh, namísto volání rozhraní API systému Windows. Tento názorný postup obsahuje informace pro tyto situace, ve které pomocí rozhraní API systému Windows je potřeba.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>Volání rozhraní API pomocí deklarace  
 Nejběžnější způsob k volání rozhraní API systému Windows je pomocí `Declare` příkaz.  
  
#### <a name="to-declare-a-dll-procedure"></a>Deklarace procedury knihovny DLL  
  
1.  Určení názvu funkce, kterou chcete volat, a navíc jeho argumenty, typy argumentů a vrátí hodnotu, jakož i název a umístění knihovny DLL, která ji obsahuje.  
  
    > [!NOTE]
    >  Úplné informace o rozhraní API systému Windows najdete v dokumentaci k Win32 SDK v rozhraní API systému Windows SDK platformy. Další informace o konstanty, které používají rozhraní API systému Windows zkontrolujte soubory hlaviček, jako je například odkazující na součástí sady SDK pro platformu Windows.  
  
2.  Otevřete nový projekt aplikace Windows tak, že kliknete na **nový** na **soubor** nabídce a potom kliknutím na **projektu**. **Nový projekt** zobrazí se dialogové okno.  
  
3.  Vyberte **aplikace Windows** ze seznamu šablon projektu jazyka Visual Basic. Zobrazí se nový projekt.  
  
4.  Přidejte následující `Declare` funkce buď ke třídě nebo modul, ve které chcete použít knihovnu DLL:  
  
     [!code-vb[VbVbalrInterop#9](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]  
  
### <a name="parts-of-the-declare-statement"></a>Součástí Declare – příkaz  
 `Declare` Příkaz obsahuje následující prvky.  
  
#### <a name="auto-modifier"></a>Automatické modifikátor  
 `Auto` Modifikátor dá pokyn modulu runtime převést řetězec na základě názvu metoda podle běžnými pravidly language runtime (nebo název aliasu-li zadána).  
  
#### <a name="lib-and-alias-keywords"></a>LIB a Alias klíčová slova  
 Tento název `Function` – klíčové slovo je název vašeho programu se používá pro přístup k importované funkce. Může být stejný jako název skutečné při volání funkce, nebo můžete použít všechny název procedury platný a poté společnosti využívají `Alias` – klíčové slovo zadat skutečné název funkce volání.  
  
 Zadejte `Lib` – klíčové slovo, za nímž následuje název a umístění knihovny DLL, která obsahuje funkce, které jsou volání. Není nutné zadat cestu pro soubory uložené v adresáři systému Windows.  
  
 Použití `Alias` – klíčové slovo název funkce při volání není platný název procedury jazyka Visual Basic nebo je v konfliktu s názvem jiných položek v aplikaci. `Alias` označuje true název funkce volána.  
  
#### <a name="argument-and-data-type-declarations"></a>Argument a deklarace typu dat  
 Deklarujte argumenty a jejich datové typy. Tuto část může být náročné, protože typy dat, které používá Windows nemusí odpovídat Visual Studio datové typy. Visual Basic nepodporuje spoustu práce pro vás převodem argumenty na kompatibilní datové typy, procesu označovaného jako *zařazování*. Můžete explicitně řídit, jak jsou argumenty zařazené pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> definovaný v atributu <xref:System.Runtime.InteropServices> oboru názvů.  
  
> [!NOTE]
>  Předchozí verze jazyka Visual Basic povolené deklarovat parametry `As Any`, tj. Tato data o všech datech typu může. Visual Basic vyžaduje použití určitého datového typu pro všechny `Declare` příkazy.  
  
#### <a name="windows-api-constants"></a>Konstanty rozhraním API systému Windows  
 Některé argumenty jsou kombinace konstanty. Například `MessageBox` rozhraní API, které jsou uvedené v tomto návodu přijímá argument celé číslo názvem `Typ` která řídí, jak se zobrazí okno se zprávou. Číselná hodnota tyto konstanty můžete určit tak, že prověří `#define` příkazy v souboru WINUSER. Číselné hodnoty jsou obecně uvedené v šestnáctkové číslo, proto je vhodné k použití kalkulačky a přidejte je převést na decimal. Například, pokud chcete kombinovat konstanty pro styl vykřičníku `MB_ICONEXCLAMATION` 0x00000030 a Ano/žádné styl `MB_YESNO` 0x00000004, můžete přidat čísla a získání výsledku 0x00000034 nebo 52 decimal. I když používáte decimal výsledek přímo, je lepší deklarovat tyto hodnoty jako konstanty ve vaší aplikaci a zkombinovat pomocí `Or` operátor.  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a>Chcete-li deklarovat konstanty pro volání rozhraní API systému Windows  
  
1.  V dokumentaci pro funkce systému Windows, ke kterému se připojujete. Určuje název, který používá konstanty a název souboru h obsahující číselné hodnoty pro tyto konstanty.  
  
2.  Pomocí textového editoru, například Poznámkový blok, chcete-li zobrazit obsah souboru hlavičky () a najděte hodnoty přidružené k konstanty, kterou používáte. Například `MessageBox` API používá rozhraní konstanta `MB_ICONQUESTION` zobrazíte otazník do pole zpráva. Definice `MB_ICONQUESTION` je ve winuser a zobrazí se následujícím způsobem:  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  Přidat ekvivalentní `Const` příkazy ke třídě nebo modul pro zpřístupnění těchto konstanty pro vaše aplikace. Příklad:  
  
     [!code-vb[VbVbalrInterop#11](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]  
  
###### <a name="to-call-the-dll-procedure"></a>Voláním procedury knihovny DLL  
  
1.  Přidání tlačítka s názvem `Button1` na spuštění tvoří pro svůj projekt a potom dvojím kliknutím zobrazit jeho kód. Obslužné rutiny události pro tlačítko se zobrazí.  
  
2.  Přidejte kód, který `Click` obslužné rutiny události pro tlačítko jste přidali, zavolejte proceduru a zadejte odpovídající argumenty:  
  
     [!code-vb[VbVbalrInterop#12](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]  
  
3.  Stisknutím klávesy F5 spusťte projekt. Do pole zpráva se zobrazí s oběma **Ano** a **ne** tlačítka odpovědi. Klikněte na některý.  
  
#### <a name="data-marshaling"></a>Dat – zařazování  
 Visual Basic automaticky převede datové typy parametry a návratové hodnoty pro volání rozhraní API systému Windows, ale můžete použít `MarshalAs` atribut k explicitnímu zadání nespravované datové typy, které očekává rozhraní API. Další informace o zařazování spolupráce najdete v tématu [zařazování zprostředkovatel komunikace s objekty](../../../framework/interop/interop-marshaling.md).  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Použití Declare a MarshalAs volání rozhraní API  
  
1.  Určení názvu funkce chcete volat plus její argumenty datových typů a vrátit hodnotu.  
  
2.  Zjednodušení přístupu k `MarshalAs` atribut, přidejte `Imports` příkaz do horní části kód pro třídu nebo modul, jako v následujícím příkladu:  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
3.  Přidejte prototyp funkce pro importované funkce ke třídě nebo modul a použít `MarshalAs` atribut parametry nebo vrací hodnotu. V následujícím příkladu volání rozhraní API, která očekává typ `void*` je zařazené jako `AsAny`:  
  
     [!code-vb[VbVbalrInterop#14](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]  
  
## <a name="api-calls-using-dllimport"></a>Volání rozhraní API pomocí příkazů DllImport  
 `DllImport` Atribut poskytuje druhý způsob, jak volat funkce v knihovnách DLL bez knihovny typů. `DllImport` zhruba odpovídá pomocí `Declare` příkaz ale nabízí větší kontrolu nad jak se označují jako funkce.  
  
 Můžete použít `DllImport` s rozhraním API systému Windows pro většinu volá tak dlouho, dokud volání odkazuje na sdílenou (někdy nazývané *statické*) metoda. Metody, které vyžadují instance třídy nelze použít. Na rozdíl od `Declare` příkazy, `DllImport` volání nelze použít `MarshalAs` atribut.  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>K volání rozhraní API systému Windows pomocí DllImport – atribut  
  
1.  Otevřete nový projekt aplikace Windows tak, že kliknete na **nový** na **soubor** nabídce a potom kliknutím na **projektu**. **Nový projekt** zobrazí se dialogové okno.  
  
2.  Vyberte **aplikace Windows** ze seznamu šablon projektu jazyka Visual Basic. Zobrazí se nový projekt.  
  
3.  Přidání tlačítka s názvem `Button2` na formulář spuštění.  
  
4.  Klikněte dvakrát na `Button2` k otevření zobrazení kódu pro daný formulář.  
  
5.  Zjednodušení přístupu k `DllImport`, přidejte `Imports` příkaz do horní části kód pro formulář třída při spuštění:  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
6.  Deklarovat prázdný funkce předchozí `End Class` příkaz pro formulář a název funkce `MoveFile`.  
  
7.  Použít `Public` a `Shared` modifikátory deklarace funkce a nastavení parametrů `MoveFile` podle argumenty funkce rozhraní API systému Windows, která používá:  
  
     [!code-vb[VbVbalrInterop#16](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]  
  
     Funkce může mít libovolný název platný postupu; `DllImport` atribut určuje název v knihovně DLL. Také obstará interoperabilita zařazování pro parametry a návratové hodnoty, abyste si mohli vybrat Visual Studio datové typy, které jsou podobné data typy používá rozhraní API.  
  
8.  Použít `DllImport` atribut funkci prázdný. První parametr je název a umístění knihovny DLL obsahující danou funkci, ke kterému se připojujete. Není nutné zadat cestu pro soubory uložené v adresáři systému Windows. Druhý parametr je pojmenovaný argument, který určuje název funkce v rozhraní API systému Windows. V tomto příkladu `DllImport` atribut vynutí volání `MoveFile` k přeposlání do `MoveFileW` v KERNEL32. KNIHOVNY DLL. `MoveFileW` Metoda zkopíruje do souboru z cesty `src` k cestě `dst`.  
  
     [!code-vb[VbVbalrInterop#17](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]  
  
9. Přidejte kód, který `Button2_Click` obslužné rutiny události pro volání funkce:  
  
     [!code-vb[VbVbalrInterop#18](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]  
  
10. Vytvořte soubor s názvem Test.txt a umístěte jej do adresáře C:\Tmp na vašem pevném disku. Vytvoření adresáře Tmp v případě potřeby.  
  
11. Stisknutím klávesy F5 a spusťte aplikaci. Zobrazí se hlavní formulář.  
  
12. Klikněte na tlačítko **Button2**. Pokud soubor můžete přesunout, zobrazí se zpráva "soubor byl úspěšně přesunut.".  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)  
 [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Vytváření prototypů ve spravovaném kódu](../../../framework/interop/creating-prototypes-in-managed-code.md)  
 [Zařazování delegáta jako metody zpětného volání](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
