---
title: 'Návod: Volání rozhraní API Windows (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 579da4b52a9a7c4c747a9ace390c04611207c94d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822905"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>Návod: Volání rozhraní API Windows (Visual Basic)
Rozhraní API Windows jsou dynamické knihovny (DLL), které jsou součástí operačního systému Windows. Můžete využít k provádění úkolů, když je obtížné je napsat ekvivalentní postupy. Například Windows poskytuje funkci s názvem `FlashWindowEx` , který umožňuje provádět alternativní mezi světlé a tmavé odstínů v záhlaví okna aplikace.  
  
 Výhodou použití rozhraní API Windows ve vašem kódu je, že se dají ušetřit dobu vývoje, protože obsahují řadě užitečných funkcí, které již byly napsány a čekáním, který se má použít. Nevýhodou je, že rozhraní API Windows může být obtížné pro práci s a nepřijímá, když něco selže.  
  
 Rozhraní Windows API představují zvláštní druh vzájemná funkční spolupráce. Rozhraní API Windows nepoužívejte spravovaného kódu, nemají integrovanou knihoven typů a používat datové typy, které se liší od používaným v sadě Visual Studio. Kvůli těmto rozdílům a protože rozhraní API Windows nejsou objekty modelu COM, vzájemná funkční spolupráce s rozhraními API pro Windows a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] se provádí pomocí platformy volání, PInvoke. Vyvolání platformy je služba, umožňuje spravovaným kódu volat nespravované funkce implementované v knihovnách DLL. Další informace najdete v tématu [používání nespravovaných funkcí DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md). PInvoke v jazyce Visual Basic můžete použít buď pomocí `Declare` příkazu nebo použití `DllImport` atribut prázdné procedury.  
  
 Volání rozhraní API Windows byly důležitou součástí jazyka Visual Basic programování v minulosti, ale jsou zřídka nezbytné v jazyce Visual Basic .NET. Kdykoli je to možné, používejte spravovanému kódu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] k provádění úloh, namísto volání rozhraní API Windows. Tento názorný postup obsahuje informace pro tyto situace, ve které pomocí rozhraní Windows API je nezbytné.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>Volání rozhraní API pomocí deklarace  
 Nejběžnější způsob volání rozhraní API Windows je použití `Declare` příkazu.  
  
#### <a name="to-declare-a-dll-procedure"></a>Chcete-li deklarovat proceduru knihovny DLL  
  
1.  Určení názvu funkce, do které chcete volat, a navíc jeho argumenty, typy argumentů a vrátí hodnotu, jakož i název a umístění knihovny DLL, která ji obsahuje.  
  
    > [!NOTE]
    >  Podrobnější informace o rozhraní API pro Windows naleznete v dokumentaci sady SDK Win32 v rozhraní API sady SDK Windows Platform. Další informace o konstanty, které používají rozhraní API pro Windows zkontrolujte soubory hlaviček, jako Windows.h, které jsou součástí sady SDK platformy.  
  
2.  Kliknutím otevřete nový projekt aplikace Windows **nový** na **souboru** nabídky a pak levým na **projektu**. Zobrazí se dialogové okno **Nový projekt**.  
  
3.  Vyberte **aplikace Windows** ze seznamu šablon projektů jazyka Visual Basic. Zobrazí se nový projekt.  
  
4.  Přidejte následující `Declare` pracovat buď pro třídu nebo modul, ve které chcete použít knihovnu DLL:  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a>Součástí Declare – příkaz  
 `Declare` Výpis obsahuje následující prvky.  
  
#### <a name="auto-modifier"></a>Modifikátor Auto  
 `Auto` Modifikátor dá pokyn modulu runtime pro převod řetězce na základě názvu metody podle toho, common language runtime pravidla (nebo název aliasu-li zadán).  
  
#### <a name="lib-and-alias-keywords"></a>Klíčová slova LIB a Alias  
 Tento název `Function` – klíčové slovo je název, který program používá pro přístup k importované funkce. Může být stejný jako skutečný název funkce, která se volá, nebo můžete použít libovolný název platný procedury a potom využívají `Alias` – klíčové slovo k určení skutečným názvem funkce, která je volá.  
  
 Zadejte `Lib` – klíčové slovo, za nímž následuje název a umístění knihovny DLL, která obsahuje funkce, která je volá. Nemusíte určit cestu pro soubory jsou umístěné v adresáři systému Windows.  
  
 Použití `Alias` – klíčové slovo název funkce při volání není platný název procedury jazyka Visual Basic, nebo je v konfliktu s názvem ostatní položky ve vaší aplikaci. `Alias` označuje true název volané funkce.  
  
#### <a name="argument-and-data-type-declarations"></a>Argument a typ deklarace dat.  
 Deklarujte argumenty a jejich datové typy. Tuto část může být náročné, protože datové typy, které používá Windows nemusí odpovídat do sady Visual Studio, datových typů. Visual Basic nepodporuje spoustu práce za vás převedením argumenty kompatibilní datové typy, proces s názvem *zařazování*. Můžete explicitně řídit, jak jsou argumenty zařadit pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributu definovanému v <xref:System.Runtime.InteropServices> oboru názvů.  
  
> [!NOTE]
>  Předchozí verzí jazyka Visual Basic umožňují deklarovat parametry `As Any`, což znamená dat jakýchkoli dat typ může použít. Visual Basic vyžaduje použití konkrétní datový typ pro všechny `Declare` příkazy.  
  
#### <a name="windows-api-constants"></a>Konstanty Windows API  
 Některé argumenty jsou kombinací konstanty. Například `MessageBox` přebírá celočíselný argument volat rozhraní API v tomto návodu `Typ` , která určuje, jak se zobrazí okno se zprávou. Můžete určit číselnou hodnotu z následujících konstant prozkoumáním `#define` příkazy v souboru WINUSER. Číselné hodnoty obecně zobrazují v šestnáctkovém formátu, takže můžete chtít použití kalkulačky a přidejte je převod na desetinnou hodnotu. Například, pokud je potřeba sloučit konstanty pro styl vykřičník `MB_ICONEXCLAMATION` 0x00000030 a Ano/žádný styl `MB_YESNO` 0x00000004, můžete přidat čísla a získat výsledek 0x00000034 nebo 52 decimal. I když používáte desítkové výsledek přímo, je lepší deklarovat tyto hodnoty jako konstanty ve vaší aplikaci a jejich kombinací pomocí `Or` operátor.  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a>Chcete-li deklarovat konstanty pro volání Windows API  
  
1.  V dokumentaci pro funkci Windows, ke kterému se připojujete. Určuje název konstanty, které používá a název souboru .h, který obsahuje číselné hodnoty pro tyto konstanty.  
  
2.  Pomocí textového editoru, jako je například Poznámkový blok, chcete-li zobrazit obsah souboru hlaviček (.h) a najděte hodnot spojené s konstanty, které používáte. Například `MessageBox` rozhraní API používá konstanta `MB_ICONQUESTION` zobrazíte otazník v okně se zprávou. Definice `MB_ICONQUESTION` je v winuser a zobrazí se takto:  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  Přidat ekvivalent `Const` příkazy na třídu nebo modul pro zpřístupnění tyto konstanty pro vaše aplikace. Příklad:  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a>K volání procedury knihovny DLL  
  
1.  Přidejte tlačítko s názvem `Button1` na počáteční formulář pro váš projekt a pak dvojím kliknutím ho zobrazte jeho kód. Zobrazí se obslužná rutina události pro tlačítko.  
  
2.  Přidejte kód, který `Click` obslužné rutiny události pro tlačítko, které jste přidali, zavolejte proceduru a poskytovat příslušnými argumenty:  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3.  Stisknutím klávesy F5 spusťte projekt. Zobrazí se okno se zprávou s oběma **Ano** a **ne** tlačítka odpovědi. Klikněte na jednu.  
  
#### <a name="data-marshaling"></a>Zařazování dat  
 Visual Basic automaticky převede datové typy parametrů a návratové hodnoty pro volání Windows API, ale můžete použít `MarshalAs` atribut s ohledem na nespravované datové typy, které se očekává, že rozhraní API. Další informace o zařazování spolupráce naleznete v tématu [zařazování Interop](../../../framework/interop/interop-marshaling.md).  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Používání Declare a MarshalAs ve volání rozhraní API  
  
1.  Určení názvu funkce, kterou chcete k volání a argumenty, datové typy a návratovou hodnotu.  
  
2.  Pro zjednodušení přístupu k `MarshalAs` atribut, přidejte `Imports` příkaz do horní části kódu pro třídu nebo modul, jako v následujícím příkladu:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3.  Přidat prototyp funkce pro importované funkce pro třídu nebo modul a použít `MarshalAs` atribut parametry nebo návratovou hodnotu. V následujícím příkladu volání rozhraní API, která očekává typ `void*` zařazena jako `AsAny`:  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a>Volání rozhraní API pomocí DllImport  
 `DllImport` Atribut obsahuje druhý způsob, jak volat funkce v knihovnách DLL bez knihovny typů. `DllImport` je zhruba ekvivalentní k použití `Declare` příkaz ale poskytuje větší kontrolu nad jakým jsou funkce volány.  
  
 Můžete použít `DllImport` s rozhraním API Windows pro většinu volání jako volání odkazuje na sdílený (říká se jim *statické*) metody. Nelze použít metody, které vyžadují instance třídy. Na rozdíl od `Declare` příkazů `DllImport` volání nelze použít `MarshalAs` atribut.  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>Pro volání Windows API pomocí atributu DllImport  
  
1.  Kliknutím otevřete nový projekt aplikace Windows **nový** na **souboru** nabídky a pak levým na **projektu**. Zobrazí se dialogové okno **Nový projekt**.  
  
2.  Vyberte **aplikace Windows** ze seznamu šablon projektů jazyka Visual Basic. Zobrazí se nový projekt.  
  
3.  Přidejte tlačítko s názvem `Button2` do formuláře při spuštění.  
  
4.  Dvakrát klikněte na panel `Button2` otevřete zobrazení kódu pro formulář.  
  
5.  Pro zjednodušení přístupu k `DllImport`, přidejte `Imports` příkaz do horní části kódu pro třídu formuláře po spuštění:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6.  Prázdná funkce předchozí deklaraci `End Class` příkaz pro formulář a název funkce `MoveFile`.  
  
7.  Použít `Public` a `Shared` modifikátory deklarace funkce a nastavit parametry pro `MoveFile` na základě argumentů funkce rozhraní Windows API používá:  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     Funkce může mít libovolný název platný postupu; `DllImport` atribut určuje název v knihovně DLL. Také obstará interoperability zařazování pro parametry a návratové hodnoty, proto můžete použít Visual Studio datové typy, které jsou podobně jako typy používá rozhraní API.  
  
8.  Použít `DllImport` atribut funkce empty. První parametr je název a umístění souboru DLL obsahujícímu funkce, který voláte. Nemusíte určit cestu pro soubory jsou umístěné v adresáři systému Windows. Druhý parametr je pojmenovaný argument, který určuje název funkce v rozhraní Windows API. V tomto příkladu `DllImport` atribut vynutí volání `MoveFile` mají být předány `MoveFileW` v KERNEL32. KNIHOVNY DLL. `MoveFileW` Metoda zkopíruje soubor z cesty `src` k cestě `dst`.  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. Přidejte kód, který `Button2_Click` obslužná rutina události volaná funkce:  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. Vytvořte soubor s názvem Test.txt a umístěte ho do C:\Tmp adresáře na pevném disku. Vytvořte adresář Tmp, v případě potřeby.  
  
11. Stisknutím klávesy F5 spusťte aplikaci. Zobrazí se hlavní formulář.  
  
12. Klikněte na tlačítko **Button2**. Pokud soubor lze přesunout, zobrazí se zpráva "soubor byl úspěšně přesunut.".  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)
- [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Vytváření prototypů ve spravovaném kódu](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [Zařazování delegáta jako metody zpětného volání](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
