---
title: 'Návod: Vložení typů ze spravovaných sestavení v aplikaci Visual Studio'
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1a37a3bcc3b1bc352d6a2f59691819e0b2403d3d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523895"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a>Návod: Vložení typů ze spravovaných sestavení v aplikaci Visual Studio

Pokud vložíte informace o typu ze spravovaného sestavení se silným názvem, můžete volně kombinovat typy v aplikaci, aby se dosáhlo nezávislosti verzí. To znamená, že program může být napsán tak, aby používal typy z jakékoli verze spravované knihovny, aniž by bylo nutné znovu kompilovat pro každou novou verzi.

Vkládání typů se často používá u zprostředkovatele komunikace s objekty COM, jako je například aplikace, která používá automatizační objekty z systém Microsoft Office. Vložení informací o typu umožňuje stejné sestavení programu pracovat s různými verzemi systém Microsoft Office v různých počítačích. Můžete ale také použít vkládání typů s plně spravovanými řešeními.

Po zadání veřejných rozhraní, která mohou být vložena, vytvoříte třídy modulu runtime, které implementují tato rozhraní. Klientský program může vložit informace o typu pro rozhraní v době návrhu odkazem na sestavení, které obsahuje veřejné rozhraní a nastavením vlastnosti `Embed Interop Types` odkazu na `True`. Klientský program pak může načíst instance objektů za běhu, které jsou zadány jako tato rozhraní. To je ekvivalentní použití kompilátoru příkazového řádku a odkazování na sestavení pomocí možnosti kompilátoru `/link`. 

Vytvoříte-li novou verzi sestavení modulu runtime se silným názvem, klientský program nebude nutné znovu kompilovat. Klientský program nadále používá, je-li k dispozici verze sestavení modulu runtime, používá informace vloženého typu pro veřejná rozhraní.

V tomto návodu:

1. Vytvořte sestavení se silným názvem pomocí veřejného rozhraní obsahujícího informace o typu, které mohou být vloženy.
1. Vytvořte sestavení modulu runtime se silným názvem, které implementuje veřejné rozhraní.
1. Vytvořte klientský program, který vloží informace o typu z veřejného rozhraní a vytvoří instanci třídy ze sestavení modulu runtime.
1. Upravte a znovu sestavte sestavení modulu runtime.
1. Spusťte klientský program, aby bylo vidět, že používá novou verzi sestavení modulu runtime, aniž by bylo nutné znovu kompilovat.

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a>Podmínky a omezení

Můžete vložit informace o typu ze sestavení za následujících podmínek: 

- Sestavení zveřejňuje alespoň jedno veřejné rozhraní.
- Vložená rozhraní jsou opatřená pomocí atributů `ComImport` a atributy `Guid` s jedinečnými identifikátory GUID.
- Sestavení je opatřeno poznámkou atributu `ImportedFromTypeLib` nebo atributem `PrimaryInteropAssembly` a atributem `Guid` na úrovni sestavení. Šablony projektů C# vizuálů a Visual Basic zahrnují ve výchozím nastavení atribut `Guid` na úrovni sestavení.

Vzhledem k tomu, že primární funkce vkládání typů je podpora sestavení COM interop, platí při vložení informací o typu do plně spravovaného řešení následující omezení:

- Jsou vložené pouze atributy specifické pro zprostředkovatele komunikace s objekty COM. Ostatní atributy se ignorují.
- Pokud typ používá obecné parametry a typ obecného parametru je vložený typ, tento typ nelze použít napříč hranicí sestavení. Příklady křížení hranice sestavení zahrnují volání metody z jiného sestavení nebo odvození typu z typu definovaného v jiném sestavení.
- Konstanty nejsou vloženy.
- Třída <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> nepodporuje vložený typ jako klíč. Můžete implementovat vlastní typ slovníku pro podporu vloženého typu jako klíče.

## <a name="create-an-interface"></a>Vytvoření rozhraní

Prvním krokem je vytvoření sestavení rozhraní rovnocennosti typů. 

1. V aplikaci Visual Studio vyberte **soubor**  > **Nový**  > **projekt**.
   
1. V dialogovém okně **vytvořit nový projekt** zadejte do pole **Hledat šablony** *knihovnu tříd* . C# V seznamu vyberte šablonu **Knihovna tříd vb (.NET Framework)** a pak vyberte **Další**. 
   
1. V dialogovém okně **Konfigurovat nový projekt** , v části **název projektu**zadejte *TypeEquivalenceInterface*a pak vyberte **vytvořit**. Vytvoří se nový projekt.
   
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor *Class1.cs* nebo *Class1. vb* , vyberte položku **Přejmenovat**a přejmenujte soubor z *Class1* na *ISampleInterface*. Chcete-li také přejmenovat třídu na `ISampleInterface`, odpovězte na výzvu **Ano** . Tato třída reprezentuje veřejné rozhraní třídy.
   
1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **TypeEquivalenceInterface** a pak vyberte **vlastnosti**. 
   
1. V levém podokně obrazovky **vlastnosti** vyberte **sestavovat** a nastavte **výstupní cestu** k umístění v počítači, například *C:\TypeEquivalenceSample*. V rámci tohoto Názorného postupu použijete stejné umístění. 
   
1. V levém podokně obrazovky **vlastnosti** vyberte **podepisování** a zaškrtněte políčko **podepsat sestavení** . V rozevíracím seznamu pro **Výběr souboru klíče se silným názvem**vyberte možnost **Nový**. 
   
1. V dialogovém okně **vytvořit klíč se silným názvem** zadejte do pole **název souboru klíče** *Key. snk*. Zrušte zaškrtnutí políčka **chránit soubor klíče heslem** a pak vyberte **OK**.
   
1. V editoru kódu otevřete soubor třídy *ISampleInterface* a nahraďte jeho obsah následujícím kódem pro vytvoření `ISampleInterface`ho rozhraní:
   
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
   
1. V nabídce **nástroje** vyberte možnost **vytvořit GUID**a v dialogovém okně **vytvořit identifikátor GUID** vyberte **Formát registru**. Vyberte možnost **Kopírovat**a pak vyberte možnost **ukončit**.
   
1. V atributu `Guid` kódu nahraďte vzorový identifikátor GUID identifikátorem GUID, který jste zkopírovali, a odeberte složené závorky ( **{}** ).
   
1. V **Průzkumník řešení**rozbalte složku **Properties (vlastnosti** ) a vyberte soubor *AssemblyInfo.cs* nebo *AssemblyInfo. vb* . V editoru kódu přidejte do souboru následující atribut:
   
   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```
   
   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```
   
1. Vyberte **soubor**  > **Uložit vše** nebo stiskněte klávesovou **zkratku CTRL** +**SHIFT** +**s** a uložte soubory a projekt.
   
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **TypeEquivalenceInterface** a vyberte možnost **sestavit**. Soubor DLL knihovny tříd je zkompilován a uložen do zadané výstupní cesty sestavení, například *C:\TypeEquivalenceSample*.

## <a name="create-a-runtime-class"></a>Vytvoření běhové třídy

Dále vytvořte třídu prostředí runtime ekvivalenci typu.

1. V aplikaci Visual Studio vyberte **soubor**  > **Nový**  > **projekt**.
   
1. V dialogovém okně **vytvořit nový projekt** zadejte do pole **Hledat šablony** *knihovnu tříd* . C# V seznamu vyberte šablonu **Knihovna tříd vb (.NET Framework)** a pak vyberte **Další**. 
   
1. V dialogovém okně **Konfigurovat nový projekt** , v části **název projektu**zadejte *TypeEquivalenceRuntime*a pak vyberte **vytvořit**. Vytvoří se nový projekt.
   
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor *Class1.cs* nebo *Class1. vb* , vyberte položku **Přejmenovat**a přejmenujte soubor z *Class1* na *SampleClass*. Chcete-li také přejmenovat třídu na `SampleClass`, odpovězte na výzvu **Ano** . Tato třída implementuje rozhraní `ISampleInterface`.
   
1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **TypeEquivalenceInterface** a vyberte **vlastnosti**. 
   
1. V levém podokně obrazovky **vlastnosti** vyberte **sestavit** a pak nastavte **výstupní cestu** ke stejnému umístění, které jste použili pro projekt TypeEquivalenceInterface, například *C:\TypeEquivalenceSample*.
   
1. V levém podokně obrazovky **vlastnosti** vyberte **podepisování** a zaškrtněte políčko **podepsat sestavení** . V rozevíracím seznamu pro **Výběr souboru klíče se silným názvem**vyberte možnost **Nový**. 
   
1. V dialogovém okně **vytvořit klíč se silným názvem** zadejte do pole **název souboru klíče** *Key. snk*. Zrušte zaškrtnutí políčka **chránit soubor klíče heslem** a pak vyberte **OK**.
   
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **TypeEquivalenceRuntime** a vyberte **Přidat**  > **odkaz**. 
   
1. V dialogovém okně **Správce odkazů** vyberte **Procházet** a přejděte do složky výstupní cesta. Vyberte soubor *TypeEquivalenceInterface. dll* , vyberte **Přidat**a pak vyberte **OK**.
   
1. V **Průzkumník řešení**rozbalte složku **odkazy** a vyberte odkaz **TypeEquivalenceInterface** . V podokně **vlastnosti** nastavte **konkrétní verzi** na **hodnotu NEPRAVDA** , pokud ještě není.
   
1. V editoru kódu otevřete soubor třídy *SampleClass* a nahraďte jeho obsah následujícím kódem pro vytvoření `SampleClass` třídy:
   
   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
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
   
1. Vyberte **soubor**  > **Uložit vše** nebo stiskněte klávesovou **zkratku CTRL** +**SHIFT** +**s** a uložte soubory a projekt.
   
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **TypeEquivalenceRuntime** a vyberte možnost **sestavit**. Soubor DLL knihovny tříd je zkompilován a uložen do zadané výstupní cesty sestavení.

## <a name="create-a-client-project"></a>Vytvořit klientský projekt

Nakonec vytvořte rovnocenný typ klientského programu, který odkazuje na sestavení rozhraní.

1. V aplikaci Visual Studio vyberte **soubor**  > **Nový**  > **projekt**.
   
1. V dialogovém okně **vytvořit nový projekt** zadejte do pole **Hledat šablony** text *Konzola* . V seznamu vyberte C# šablonu **Konzolová aplikace nebo aplikace VB (.NET Framework)** a pak vyberte **Další**. 
   
1. V dialogovém okně **Konfigurovat nový projekt** , v části **název projektu**zadejte *TypeEquivalenceClient*a pak vyberte **vytvořit**. Vytvoří se nový projekt.
   
1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **TypeEquivalenceClient** a vyberte **vlastnosti**. 
   
1. V levém podokně obrazovky **vlastnosti** vyberte **sestavit** a pak nastavte **výstupní cestu** ke stejnému umístění, které jste použili pro projekt TypeEquivalenceInterface, například *C:\TypeEquivalenceSample*.
   
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **TypeEquivalenceClient** a vyberte **Přidat**  > **odkaz**. 
   
1. Pokud je soubor **TypeEquivalenceInterface. dll** již v dialogovém okně **Správce odkazů** uveden, vyberte jej. Pokud ne, vyberte **Procházet**, přejděte do složky výstupní cesta, vyberte soubor *TypeEquivalenceInterface. dll* (ne *TypeEquivalenceRuntime. dll*) a vyberte **Přidat**. Vyberte **OK**.
   
1. V **Průzkumník řešení**rozbalte složku **odkazy** a vyberte odkaz **TypeEquivalenceInterface** . V podokně **Vlastnosti nastavte možnosti** **Vložit typy spolupráce** na **hodnotu true**.
   
1. Otevřete soubor *program.cs* nebo *Module1. vb* v editoru kódu a nahraďte jeho obsah následujícím kódem pro vytvoření klientského programu:
   
   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using TypeEquivalenceInterface;
   using System.Reflection;
   
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
   Imports TypeEquivalenceInterface
   Imports System.Reflection
   
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
   
1. Vyberte **soubor**  > **Uložit vše** nebo stiskněte klávesovou **zkratku CTRL** +**SHIFT** +**s** a uložte soubory a projekt.
   
1. Stisknutím **kombinace kláves Ctrl** +**F5** Sestavte a spusťte program. Všimněte si, že výstup konzoly vrátí sestavení verze **1.0.0.0**. 
   
## <a name="modify-the-interface"></a>Změna rozhraní

Nyní upravte sestavení rozhraní a změňte jeho verzi. 

1. V aplikaci Visual Studio vyberte **soubor**  > **otevřete**  > **projekt/řešení**a otevřete projekt **TypeEquivalenceInterface** .
   
1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **TypeEquivalenceInterface** a vyberte **vlastnosti**. 
   
1. V levém podokně obrazovky **vlastnosti** vyberte **aplikace** a pak vyberte **informace o sestavení**. 
   
1. V dialogovém okně **informace o sestavení** změňte **verzi sestavení** a hodnoty **verze souboru** na *2.0.0.0*a pak vyberte **OK**.
   
1. Otevřete soubor *SampleInterface.cs* nebo *SampleInterface. vb* a přidejte následující řádek kódu do `ISampleInterface` rozhraní:
   
   ```csharp
   DateTime GetDate();
   ```
   
   ```vb
   Function GetDate() As Date
   ```
   
1. Vyberte **soubor**  > **Uložit vše** nebo stiskněte klávesovou **zkratku CTRL** +**SHIFT** +**s** a uložte soubory a projekt.
   
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **TypeEquivalenceInterface** a vyberte možnost **sestavit**. Nová verze souboru DLL knihovny tříd je zkompilována a uložena do výstupní cesty sestavení.

## <a name="modify-the-runtime-class"></a>Úprava běhové třídy

Také upravte třídu modulu runtime a aktualizujte její verzi. 

1. V aplikaci Visual Studio vyberte **soubor**  > **otevřete**  > **projekt/řešení**a otevřete projekt **TypeEquivalenceRuntime** .
   
1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **TypeEquivalenceRuntime** a vyberte **vlastnosti**. 
   
1. V levém podokně obrazovky **vlastnosti** vyberte **aplikace** a pak vyberte **informace o sestavení**. 
   
1. V dialogovém okně **informace o sestavení** změňte **verzi sestavení** a hodnoty **verze souboru** na *2.0.0.0*a pak vyberte **OK**.
   
1. Otevřete soubor *SampleClass.cs* nebo *SampleClass. vb* a přidejte následující kód do třídy `SampleClass`:
   
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
   
1. Vyberte **soubor**  > **Uložit vše** nebo stiskněte klávesovou **zkratku CTRL** +**SHIFT** +**s** a uložte soubory a projekt.
   
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **TypeEquivalenceRuntime** a vyberte možnost **sestavit**. Nová verze souboru DLL knihovny tříd je zkompilována a uložena do výstupní cesty sestavení.

## <a name="run-the-updated-client-program"></a>Spustit aktualizovaný klientský program 

Přejít do umístění výstupní složky sestavení a spustit *TypeEquivalenceClient. exe*. Všimněte si, že výstup konzoly nyní odráží novou verzi `TypeEquivalenceRuntime` sestavení *2.0.0.0*, aniž by byl program znovu zkompilován.

## <a name="see-also"></a>Viz také:

- [-Link (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
- [C#Průvodce programováním](../../csharp/programming-guide/index.md)
- [Koncepty programování (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Program se sestaveními](program.md)
- [Sestavení v .NET](index.md)
