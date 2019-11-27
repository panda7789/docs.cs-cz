---
title: 'Návod: Volání rozhraní API systému Windows'
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
ms.openlocfilehash: ec6b8ddc8769fadde52aaebd6ad3701183fac77a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74338669"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>Návod: Volání rozhraní API systému Windows (Visual Basic)
Rozhraní API systému Windows jsou dynamické knihovny (DLL), které jsou součástí operačního systému Windows. Můžete je používat k provádění úkolů, když je obtížné psát ekvivalentní procedury vlastní. Například systém Windows poskytuje funkci s názvem `FlashWindowEx`, která umožňuje nastavit záhlaví pro alternativní použití mezi světlými a tmavými odstíny.  
  
 Výhodou použití rozhraní API systému Windows ve vašem kódu je, že mohou ušetřit čas vývoje, protože obsahují desítky užitečných funkcí, které již byly zapsány a čekají na jejich použití. Nevýhodou je, že rozhraní API systému Windows může být obtížné pracovat s a unforgiving, když se něco nepodaří.  
  
 Rozhraní API systému Windows představuje zvláštní kategorii interoperability. Rozhraní API systému Windows nepoužívají spravovaný kód, nemají předdefinované knihovny typů a používají datové typy, které se liší od těch, které se používají se sadou Visual Studio. Z důvodu těchto rozdílů a protože rozhraní API systému Windows nejsou objekty COM, interoperabilita s rozhraními API systému Windows a .NET Framework se provádí pomocí vyvolání platformy nebo PInvoke. Vyvolání platformy je služba, která umožňuje spravovanému kódu volat nespravované funkce implementované v knihovnách DLL. Další informace naleznete v tématu [spotřebovávání nespravovaných funkcí DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md). PInvoke v Visual Basic lze použít buď pomocí příkazu `Declare`, nebo použitím atributu `DllImport` na prázdnou proceduru.  
  
 Volání rozhraní API systému Windows byla důležitou součástí Visual Basicho programování v minulosti, ale není to zřídka nutné pro Visual Basic .NET. Kdykoli je to možné, měli byste použít spravovaný kód z .NET Framework k provádění úloh místo volání rozhraní API systému Windows. Tento návod poskytuje informace pro případy, kdy je nutné použít rozhraní API systému Windows.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>Volání rozhraní API pomocí příkazu Declare  
 Nejběžnější způsob, jak volat rozhraní API systému Windows, je použití příkazu `Declare`.  
  
### <a name="to-declare-a-dll-procedure"></a>Deklarace procedury DLL  
  
1. Určete název funkce, kterou chcete volat, včetně jejích argumentů, typů argumentů a návratové hodnoty, a také název a umístění knihovny DLL, která ho obsahuje.  
  
    > [!NOTE]
    > Úplné informace o rozhraních API systému Windows naleznete v dokumentaci k Win32 SDK v rozhraní API platformy Windows API. Další informace o konstantách, které používají rozhraní Windows API, najdete v hlavičkových souborech, jako je Windows. h, které jsou součástí sady SDK platformy.  
  
2. Otevřete nový projekt aplikace pro Windows kliknutím na **Nový** v nabídce **soubor** a potom klikněte na **projekt**. Zobrazí se dialogové okno **Nový projekt** .  
  
3. V seznamu Visual Basic šablon projektů vyberte možnost **aplikace systému Windows** . Zobrazí se nový projekt.  
  
4. Přidejte následující funkci `Declare` buď do třídy, nebo modulu, ve kterém chcete použít knihovnu DLL:  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a>Části příkazu Declare  
 Příkaz `Declare` obsahuje následující prvky.  
  
#### <a name="auto-modifier"></a>Automatický modifikátor  
 Modifikátor `Auto` instruuje modul runtime, aby převedl řetězec na základě názvu metody podle pravidel společného jazykového modulu runtime (nebo název aliasu, je-li zadán).  
  
#### <a name="lib-and-alias-keywords"></a>Lib a klíčová slova aliasů  
 Název následující po klíčovém slovu `Function` je název, který program používá pro přístup k importované funkci. Může to být stejný jako skutečný název volané funkce, nebo můžete použít libovolný platný název procedury a potom pomocí klíčového slova `Alias` zadat skutečný název volané funkce.  
  
 Zadejte klíčové slovo `Lib` následovaný názvem a umístěním knihovny DLL, která obsahuje funkci, kterou voláte. Nemusíte zadávat cestu k souborům umístěným v adresářích systému Windows.  
  
 Klíčové slovo `Alias` použijte v případě, že název volané funkce není platný název Visual Basic procedury nebo je v konfliktu s názvem dalších položek v aplikaci. `Alias` označuje skutečný název volané funkce.  
  
#### <a name="argument-and-data-type-declarations"></a>Deklarace argumentů a datových typů  
 Deklarujte argumenty a jejich datové typy. Tato část může být náročná, protože datové typy, které systém Windows používá, neodpovídají datovým typům sady Visual Studio. Visual Basic provede mnoho práce za vás převodem argumentů na kompatibilní datové typy, což je proces nazvaný *zařazování*. Můžete explicitně řídit, jak jsou argumenty zařazeny pomocí atributu <xref:System.Runtime.InteropServices.MarshalAsAttribute> definovaného v oboru názvů <xref:System.Runtime.InteropServices>.  
  
> [!NOTE]
> Předchozí verze Visual Basic umožňují deklarovat parametry `As Any`, což znamená, že je možné použít data libovolného datového typu. Visual Basic vyžaduje, abyste pro všechny příkazy `Declare` používali určitý datový typ.  
  
#### <a name="windows-api-constants"></a>Konstanty rozhraní API systému Windows  
 Některé argumenty představují kombinace konstant. Například rozhraní API `MessageBox` zobrazené v tomto návodu přijímá celočíselný argument nazvaný `Typ`, který určuje, jak se okno se zprávou zobrazuje. Číselnou hodnotu těchto konstant můžete určit prozkoumáním příkazů `#define` v souboru WinUser. h. Číselné hodnoty jsou obecně zobrazeny v hexadecimálním formátu, takže můžete chtít použít kalkulačku pro jejich přidání a převod na desetinné číslo. Například pokud chcete kombinovat konstanty pro typ vykřičník `MB_ICONEXCLAMATION` 0x00000030 a styl ano/ne `MB_YESNO` 0x00000004, můžete přidat čísla a získat výsledek 0x00000034 nebo desítkového čísla 52. I když můžete použít výsledek Decimal přímo, je lepší deklarovat tyto hodnoty jako konstanty ve vaší aplikaci a kombinovat je pomocí operátoru `Or`.  
  
##### <a name="to-declare-constants-for-windows-api-calls"></a>Deklarace konstant pro volání rozhraní API systému Windows  
  
1. Projděte si dokumentaci pro funkci Windows, kterou voláte. Určete název konstant, které používá, a název souboru. h, který obsahuje číselné hodnoty pro tyto konstanty.  
  
2. Použijte textový editor, například Poznámkový blok, k zobrazení obsahu souboru hlaviček (. h) a vyhledejte hodnoty přidružené k konstantám, které používáte. Rozhraní `MessageBox` API například používá konstantu `MB_ICONQUESTION` k zobrazení otazníku v okně se zprávou. Definice pro `MB_ICONQUESTION` je v WinUser. h a vypadá takto:  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3. Přidejte ekvivalentní příkazy `Const` do třídy nebo modulu, aby byly tyto konstanty k dispozici pro vaši aplikaci. Příklad:  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a>Volání procedury DLL  
  
1. Přidejte tlačítko s názvem `Button1` do formuláře po spuštění pro váš projekt a pak dvakrát klikněte na něj pro zobrazení kódu. Zobrazí se obslužná rutina události pro tlačítko.  
  
2. Přidejte kód do obslužné rutiny události `Click` pro tlačítko, které jste přidali, pro volání procedury a poskytněte příslušné argumenty:  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3. Spusťte projekt stisknutím klávesy F5. Okno se zprávou se zobrazí s tlačítky **Ano** i **bez** odpovědi. Klikněte na jednu z těchto.  
  
#### <a name="data-marshaling"></a>Zařazování dat  
 Visual Basic automaticky převádí datové typy parametrů a návratové hodnoty pro volání rozhraní API systému Windows, ale můžete použít atribut `MarshalAs` k explicitnímu zadání nespravovaných datových typů, které rozhraní API očekává. Další informace o interop marshaling najdete v tématu [zařazování Interop](../../../framework/interop/interop-marshaling.md).  
  
##### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Použití příkazu Declare a MarshalAs v volání rozhraní API  
  
1. Určete název funkce, kterou chcete volat, včetně jejích argumentů, datových typů a návratové hodnoty.  
  
2. Chcete-li zjednodušit přístup k atributu `MarshalAs`, přidejte příkaz `Imports` na začátek kódu pro třídu nebo modul, jako v následujícím příkladu:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3. Přidejte prototyp funkce pro importovanou funkci do třídy nebo modulu, který používáte, a použijte atribut `MarshalAs` pro parametry nebo návratovou hodnotu. V následujícím příkladu je volání rozhraní API, které očekává typ `void*`, zařazeno jako `AsAny`:  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a>Volání rozhraní API pomocí DllImport  
 Atribut `DllImport` poskytuje druhý způsob volání funkcí v knihovnách DLL bez knihoven typů. `DllImport` je zhruba ekvivalentní použití příkazu `Declare`, ale poskytuje lepší kontrolu nad tím, jak jsou funkce volány.  
  
 Můžete použít `DllImport` u většiny volání rozhraní API systému Windows, pokud volání odkazuje na sdílenou (někdy označovanou jako *statickou*) metodu. Nemůžete použít metody, které vyžadují instanci třídy. Na rozdíl od příkazů `Declare` nemůže `DllImport` volání používat atribut `MarshalAs`.  
  
### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>Volání rozhraní API systému Windows pomocí atributu DllImport  
  
1. Otevřete nový projekt aplikace pro Windows kliknutím na **Nový** v nabídce **soubor** a potom klikněte na **projekt**. Zobrazí se dialogové okno **Nový projekt** .  
  
2. V seznamu Visual Basic šablon projektů vyberte možnost **aplikace systému Windows** . Zobrazí se nový projekt.  
  
3. Přidejte tlačítko s názvem `Button2` do formuláře po spuštění.  
  
4. Dvojím kliknutím na `Button2` otevřete zobrazení kódu pro formulář.  
  
5. Chcete-li zjednodušit přístup k `DllImport`, přidejte příkaz `Imports` do horní části kódu pro třídu formuláře po spuštění:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6. Deklarujte prázdnou funkci před příkazem `End Class` pro formulář a pojmenujte funkci `MoveFile`.  
  
7. Použijte modifikátory `Public` a `Shared` na deklaraci funkce a nastavte parametry pro `MoveFile` na základě argumentů, které funkce rozhraní API systému Windows používá:  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     Vaše funkce může mít libovolný platný název procedury; atribut `DllImport` Určuje název v knihovně DLL. Také zpracovává zařazování interoperability pro parametry a návratové hodnoty, takže můžete zvolit datové typy sady Visual Studio, které jsou podobné datovým typům, které používá rozhraní API.  
  
8. Použijte atribut `DllImport` pro prázdnou funkci. První parametr je název a umístění knihovny DLL obsahující funkci, kterou voláte. Nemusíte zadávat cestu k souborům umístěným v adresářích systému Windows. Druhý parametr je pojmenovaný argument, který určuje název funkce v rozhraní API systému Windows. V tomto příkladu atribut `DllImport` vynutí volání `MoveFile` přesměrování do `MoveFileW` v KERNEL32. DLL. Metoda `MoveFileW` zkopíruje soubor z cesty `src` do cesty `dst`.  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. Přidejte kód do obslužné rutiny události `Button2_Click` pro volání funkce:  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. Vytvořte soubor s názvem test. txt a umístěte ho do adresáře C:\Tmp na pevném disku. V případě potřeby vytvořte adresář tmp.  
  
11. Stisknutím klávesy F5 spusťte aplikaci. Zobrazí se hlavní formulář.  
  
12. Klikněte na možnost **Button2**. Zpráva "soubor byl úspěšně přesunut" se zobrazí, pokud jej lze přesunout.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Zástupný](../../../visual-basic/language-reference/statements/alias-clause.md)
- [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Vytváření prototypů ve spravovaném kódu](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [Zařazování delegáta jako metody zpětného volání](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
