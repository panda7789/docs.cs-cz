---
title: 'Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio'
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: f11fbedad766753ee462c5f597b823493cdaf7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75338560"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a>Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio

Pokud vložíte informace o typu ze spravovaného sestavení se silným názvem, můžete volně spárovat typy v aplikaci, abyste dosáhli nezávislosti verze. To znamená, že váš program může být zapsán do použití typů z libovolné verze spravované knihovny bez nutnosti překompilovat pro každou novou verzi.

Vkládání typů se často používá s interop modelu COM, například s aplikací, která používá objekty automatizace z aplikace Microsoft Office. Vkládání informací o typu umožňuje stejné sestavení programu pracovat s různými verzemi sady Microsoft Office v různých počítačích. Můžete však také použít vkládání typů s plně spravovanými řešeními.

Po zadání veřejných rozhraní, které mohou být vloženy, vytvoříte runtime třídy, které implementují tato rozhraní. Klientský program může vložit informace o typu rozhraní v době návrhu odkazem na sestavení, které obsahuje veřejná rozhraní a nastavení `Embed Interop Types` vlastnosti odkazu na `True`. Klientský program pak může načíst instance objektů runtime zadaných jako tato rozhraní. To je ekvivalentní použití kompilátoru příkazového řádku a odkazování na sestavení pomocí [možnosti kompilátoru -link](../../csharp/language-reference/compiler-options/link-compiler-option.md).

Pokud vytvoříte novou verzi sestavení runtime se silným názvem, klientský program nemusí být znovu zkompilován. Klientský program nadále používá kteroukoli verzi sestavení modulu runtime, která je mu k dispozici, pomocí informací o vloženém typu pro veřejná rozhraní.

V tomto návodu:

1. Vytvořte sestavení se silným názvem s veřejným rozhraním obsahujícím informace o typu, které lze vložit.
1. Vytvořte sestavení modulu runtime se silným názvem, které implementuje veřejné rozhraní.
1. Vytvořte klientský program, který vloží informace o typu z veřejného rozhraní a vytvoří instanci třídy ze sestavení modulu runtime.
1. Upravte a znovu vytvořte sestavení za běhu.
1. Spusťte klientský program a zjistěte, že používá novou verzi sestavení runtime bez nutnosti opětovné kompilace.

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a>Podmínky a omezení

Informace o typu můžete vložit ze sestavy za následujících podmínek:

- Sestavení zpřístupňuje alespoň jedno veřejné rozhraní.
- Vložená rozhraní jsou anotována `ComImport` s `Guid` atributy a atributy s jedinečnými identifikátory GUID.
- Sestavení je anotováno `ImportedFromTypeLib` atributem `PrimaryInteropAssembly` nebo atributem a `Guid` atributem na úrovni sestavení. Šablony projektu Visual C# a Visual Basic `Guid` obsahují ve výchozím nastavení atribut na úrovni sestavení.

Vzhledem k tomu, že primární funkcí vkládání typu je podpora sestavení interop com, platí následující omezení při vložení informací o typu do plně spravovaného řešení:

- Vloženy jsou pouze atributy specifické pro interop com. Ostatní atributy jsou ignorovány.
- Pokud typ používá obecné parametry a typ obecného parametru je vložený typ, nelze tento typ použít přes hranice sestavení. Příklady křížení hranice sestavy zahrnují volání metody z jiné sestavy nebo odvození typu z typu definovaného v jiné sestavě.
- Konstanty nejsou vloženy.
- Třída <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> nepodporuje vložený typ jako klíč. Můžete implementovat vlastní typ slovníku pro podporu vloženého typu jako klíč.

## <a name="create-an-interface"></a>Vytvoření rozhraní

Prvním krokem je vytvoření sestavení rozhraní rovnocennosti typu.

1. V sadě Visual Studio vyberte **Soubor** > **nový** > **projekt**.

1. V **dialogovém** okně Vytvořit nový projekt zadejte *knihovnu tříd* do pole **Hledat šablony.** Vyberte šablonu knihovny tříd jazyka C# nebo Visual Basic **(.NET Framework)** ze seznamu a pak vyberte **Další**.

1. V dialogovém okně **Konfigurovat nový projekt** v části Název **projektu**zadejte *typ TypeEquivalenceInterface*a pak vyberte **Vytvořit**. Nový projekt je vytvořen.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na soubor *Class1.cs* nebo *Class1.vb,* vyberte **přejmenovat**a přejmenujte soubor z *třídy 1* na *ISampleInterface*. Odpověď **Ano** na výzvu a přejmenujte třídu také na `ISampleInterface`. Tato třída představuje veřejné rozhraní pro třídu.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceInterface** a vyberte příkaz **Vlastnosti**.

1. Vyberte **Možnost Sestavovat** v levém podokně obrazovky **Vlastnosti** a nastavte **výstupní cestu** do umístění v počítači, například *C:\TypeEquivalenceSample*. V tomto návodu se používá stejné umístění.

1. V levém podokně obrazovky **Vlastnosti** vyberte **Podepisování** a zaškrtněte políčko **Podepsat sestavení.** V rozevíracím dokumentu **V části Zvolte soubor klíče silného názvu**vyberte **Nový**.

1. V dialogovém okně **Vytvořit silný klíč názvu** zadejte v části Název **souboru klíče příkaz** *key.snk*. Zrušte zaškrtnutí **políčka Zamknout soubor klíče heslem** a pak vyberte **OK**.

1. Otevřete soubor třídy *ISampleInterface* v editoru kódu a nahraďte jeho obsah následujícím kódem `ISampleInterface` pro vytvoření rozhraní:

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   namespace TypeEquivalenceInterface
   {
       [ComImport]
       [Guid("8DA56996-A151-4136-B474-32784559F6DF")]
       public interface ISampleInterface
       {
           void GetUserInput();
           string UserInput { get; }
       }
   }
   ```

   ```vb
   Imports System.Runtime.InteropServices

   <ComImport()>
   <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
   Public Interface ISampleInterface
       Sub GetUserInput()
       ReadOnly Property UserInput As String
   End Interface
   ```

1. V nabídce **Nástroje** vyberte **Vytvořit identifikátor GUI**a v dialogovém okně Vytvořit identifikátor **GUID** vyberte **Formát registru**. Vyberte **Kopírovat**a pak vyberte **Ukončit**.

1. V `Guid` atributu kódu nahraďte ukázkový identifikátor GUID zkopírovaným identifikátorem GUID a odeberte závorky (**{ }**).

1. V **Průzkumníku řešení**rozbalte složku **Vlastnosti** a vyberte soubor *AssemblyInfo.cs* nebo *AssemblyInfo.vb.* V editoru kódu přidejte do souboru následující atribut:

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. Vyberte **Uložit** > **vše** nebo stisknutím **klávesy Ctrl**+**Shift**+**S** uložte soubory a projekt.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceInterface** a vyberte **příkaz Build**. Soubor Knihovny dll knihovny tříd je zkompilován a uložen do zadané cesty výstupu sestavení, například *C:\TypeEquivalenceSample*.

## <a name="create-a-runtime-class"></a>Vytvoření runtime třídy

Dále vytvořte třídu runtime ekvivalence typu.

1. V sadě Visual Studio vyberte **Soubor** > **nový** > **projekt**.

1. V **dialogovém** okně Vytvořit nový projekt zadejte *knihovnu tříd* do pole **Hledat šablony.** Vyberte šablonu knihovny tříd jazyka C# nebo Visual Basic **(.NET Framework)** ze seznamu a pak vyberte **Další**.

1. V dialogovém okně **Konfigurovat nový projekt** v části Název **projektu**zadejte *typ TypEquivalenceRuntime*a pak vyberte **Vytvořit**. Nový projekt je vytvořen.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na soubor *Class1.cs* nebo *Class1.vb,* vyberte **přejmenovat**a přejmenujte soubor z *Třídy1* na *SampleClass*. Odpověď **Ano** na výzvu a přejmenujte třídu také na `SampleClass`. Tato třída implementuje `ISampleInterface` rozhraní.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceInterface** a vyberte příkaz **Vlastnosti**.

1. Vyberte **Možnost Sestavovat** v levém podokně obrazovky **Vlastnosti** a pak nastavte **výstupní cestu** do stejného umístění, jaké jste použili pro projekt TypeEquivalenceInterface, například *C:\TypeEquivalenceSample*.

1. V levém podokně obrazovky **Vlastnosti** vyberte **Podepisování** a zaškrtněte políčko **Podepsat sestavení.** V rozevíracím dokumentu **V části Zvolte soubor klíče silného názvu**vyberte **Nový**.

1. V dialogovém okně **Vytvořit silný klíč názvu** zadejte v části Název **souboru klíče příkaz** *key.snk*. Zrušte zaškrtnutí **políčka Zamknout soubor klíče heslem** a pak vyberte **OK**.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceRuntime** a vyberte **příkaz Přidat** > **odkaz**.

1. V dialogovém okně **Správce odkazů** vyberte **Procházet** a vyhledejte složku výstupní cesty. Vyberte soubor *TypeEquivalenceInterface.dll,* vyberte **Přidat**a pak vyberte **OK**.

1. V **Průzkumníku řešení**rozbalte složku **Reference a** vyberte odkaz **TypeEquivalenceInterface.** V podokně **Vlastnosti** nastavte **konkrétní verzi** na **hodnotu False,** pokud ještě není.

1. Otevřete soubor třídy *SampleClass* v editoru kódu a nahraďte jeho obsah následujícím kódem `SampleClass` pro vytvoření třídy:

   ```csharp
   using System;
   using TypeEquivalenceInterface;

   namespace TypeEquivalenceRuntime
   {
       public class SampleClass : ISampleInterface
       {
           private string p_UserInput;
           public string UserInput { get { return p_UserInput; } }

           public void GetUserInput()
           {
               Console.WriteLine("Please enter a value:");
               p_UserInput = Console.ReadLine();
           }
       }
   }
   ```

   ```vb
   Imports TypeEquivalenceInterface

   Public Class SampleClass
       Implements ISampleInterface

       Private p_UserInput As String
       Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput
           Get
               Return p_UserInput
           End Get
       End Property

       Public Sub GetUserInput() Implements ISampleInterface.GetUserInput
           Console.WriteLine("Please enter a value:")
           p_UserInput = Console.ReadLine()
       End Sub
   End Class
   ```

1. Vyberte **Uložit** > **vše** nebo stisknutím **klávesy Ctrl**+**Shift**+**S** uložte soubory a projekt.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceRuntime** a vyberte **příkaz Build**. Soubor DLL knihovny tříd je zkompilován a uložen do zadané cesty výstupu sestavení.

## <a name="create-a-client-project"></a>Vytvoření klientského projektu

Nakonec vytvořte klientský program ekvivalence typu, který odkazuje na sestavení rozhraní.

1. V sadě Visual Studio vyberte **Soubor** > **nový** > **projekt**.

1. V **dialogovém** okně Vytvořit nový projekt zadejte *konzolu* do pole **Hledat šablony.** Vyberte šablonu konzoly C# nebo Visual Basic **Console App (.NET Framework)** ze seznamu a pak vyberte **Další**.

1. V dialogovém okně **Konfigurovat nový projekt** v části Název **projektu**zadejte *typ TypuEquivalenceClient*a pak vyberte **Vytvořit**. Nový projekt je vytvořen.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceClient** a vyberte příkaz **Vlastnosti**.

1. Vyberte **Možnost Sestavovat** v levém podokně obrazovky **Vlastnosti** a pak nastavte **výstupní cestu** do stejného umístění, jaké jste použili pro projekt TypeEquivalenceInterface, například *C:\TypeEquivalenceSample*.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceClient** a vyberte **příkaz Přidat** > **odkaz**.

1. Pokud je v dialogovém **okně Správce odkazů** soubor **TypeEquivalenceInterface.dll** již uveden, vyberte jej. Pokud ne, vyberte **Procházet**, vyhledejte složku výstupní cesty, vyberte soubor *TypeEquivalenceInterface.dll* (nikoli *TypeEquivalenceRuntime.dll*) a vyberte **Přidat**. Vyberte **OK**.

1. V **Průzkumníku řešení**rozbalte složku **Reference a** vyberte odkaz **TypeEquivalenceInterface.** V podokně **Vlastnosti** nastavte **vložit typy interop** na **hodnotu True**.

1. Otevřete soubor *Program.cs* nebo *Module1.vb* v editoru kódu a nahraďte jeho obsah následujícím kódem pro vytvoření klientského programu:

   ```csharp
   using System;
   using System.Reflection;
   using TypeEquivalenceInterface;

   namespace TypeEquivalenceClient
   {
       class Program
       {
           static void Main(string[] args)
           {
               Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");
               ISampleInterface sampleClass =
                   (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");
               sampleClass.GetUserInput();
               Console.WriteLine(sampleClass.UserInput);
               Console.WriteLine(sampleAssembly.GetName().Version.ToString());
               Console.ReadLine();
           }
       }
   }
   ```

   ```vb
   Imports System.Reflection
   Imports TypeEquivalenceInterface

   Module Module1

       Sub Main()
           Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")
           Dim sampleClass As ISampleInterface = CType( _
               sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)
           sampleClass.GetUserInput()
           Console.WriteLine(sampleClass.UserInput)
           Console.WriteLine(sampleAssembly.GetName().Version)
           Console.ReadLine()
       End Sub

   End Module
   ```

1. Vyberte **Uložit** > **vše** nebo stisknutím **klávesy Ctrl**+**Shift**+**S** uložte soubory a projekt.

1. Stisknutím **klávesy Ctrl**+**F5** vytvořte a spusťte program. Všimněte si, že výstup konzoly vrátí verzi sestavení **1.0.0.0**.

## <a name="modify-the-interface"></a>Úprava rozhraní

Nyní upravte sestavení rozhraní a změňte jeho verzi.

1. V sadě Visual Studio vyberte **soubor** > **otevřít** > **projekt/řešení**a otevřete projekt **TypeEquivalenceInterface.**

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceInterface** a vyberte příkaz **Vlastnosti**.

1. V levém podokně obrazovky **Vlastnosti** vyberte **Aplikace** a pak vyberte Informace **o sestavení**.

1. V dialogovém okně **Informace o sestavení** změňte hodnoty verze **sestavení** a **verze souboru** na *2.0.0.0*a pak vyberte **OK**.

1. Otevřete soubor *SampleInterface.cs* nebo *SampleInterface.vb* a do `ISampleInterface` rozhraní přidejte následující řádek kódu:

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. Vyberte **Uložit** > **vše** nebo stisknutím **klávesy Ctrl**+**Shift**+**S** uložte soubory a projekt.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceInterface** a vyberte **příkaz Build**. Nová verze souboru DLL knihovny tříd je zkompilován a uložena do cesty výstupu sestavení.

## <a name="modify-the-runtime-class"></a>Úprava třídy runtime

Upravte také třídu runtime a aktualizujte její verzi.

1. V sadě Visual Studio vyberte **soubor** > **otevřít** > **projekt/řešení**a otevřete projekt **TypeEquivalenceRuntime.**

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceRuntime** a vyberte příkaz **Vlastnosti**.

1. V levém podokně obrazovky **Vlastnosti** vyberte **Aplikace** a pak vyberte Informace **o sestavení**.

1. V dialogovém okně **Informace o sestavení** změňte hodnoty verze **sestavení** a **verze souboru** na *2.0.0.0*a pak vyberte **OK**.

1. Otevřete soubor *SampleClass.cs* nebo *SampleClass.vb* a přidejte do `SampleClass` třídy následující kód:

   ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
   ```

   ```vb
   Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
       Return Now
   End Function
   ```

1. Vyberte **Uložit** > **vše** nebo stisknutím **klávesy Ctrl**+**Shift**+**S** uložte soubory a projekt.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceRuntime** a vyberte **příkaz Build**. Nová verze souboru DLL knihovny tříd je zkompilován a uložena do cesty výstupu sestavení.

## <a name="run-the-updated-client-program"></a>Spuštění aktualizovaného klientského programu

Přejděte do umístění výstupní složky sestavení a spusťte *soubor TypeEquivalenceClient.exe*. Všimněte si, že výstup konzoly `TypeEquivalenceRuntime` nyní odráží novou verzi sestavení, *2.0.0.0*, bez překompilován programu.

## <a name="see-also"></a>Viz také

- [-link (Možnosti kompilátoru Jazyka C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
- [Průvodce programováním v C#](../../csharp/programming-guide/index.md)
- [Koncepty programování (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Sestavení v .NET](index.md)
