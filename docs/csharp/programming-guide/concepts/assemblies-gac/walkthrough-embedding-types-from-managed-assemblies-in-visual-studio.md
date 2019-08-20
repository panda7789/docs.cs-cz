---
title: 'Návod: Vložení typů ze spravovaných sestavení v aplikaci Visual StudioC#()'
ms.date: 07/20/2015
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
ms.openlocfilehash: 5e6494f133128e3982aa07323d2c65b9fa5de47b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595805"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a>Návod: Vložení typů ze spravovaných sestavení v aplikaci Visual StudioC#()

Pokud vložíte informace o typu ze spravovaného sestavení se silným názvem, můžete volně kombinovat typy v aplikaci, aby se dosáhlo nezávislosti verzí. To znamená, že program může být napsán tak, aby používal typy z více verzí spravované knihovny, aniž by bylo nutné znovu kompilovat pro každou verzi.

Vkládání typů se často používá u zprostředkovatele komunikace s objekty COM, jako je například aplikace, která používá automatizační objekty z systém Microsoft Office. Vložení informací o typu umožňuje stejné sestavení programu pracovat s různými verzemi systém Microsoft Office v různých počítačích. Můžete však také použít vkládání typů s plně spravovaným řešením.

Informace o typu mohou být vloženy ze sestavení, které má následující vlastnosti:

- Sestavení zveřejňuje alespoň jedno veřejné rozhraní.

- Vložená rozhraní jsou opatřena `ComImport` atributem `Guid` a atributem (a jedinečným identifikátorem GUID).

- Sestavení je opatřeno poznámkou `ImportedFromTypeLib` s atributem `PrimaryInteropAssembly` nebo atributem a atributem na `Guid` úrovni sestavení. (Ve výchozím nastavení šablony C# Visual Projectu zahrnují atribut na úrovni `Guid` sestavení.)

Po zadání veřejných rozhraní, která lze vložit, můžete vytvořit třídy modulu runtime, které implementují tato rozhraní. Klientský program pak může vložit informace o typu pro tato rozhraní v době návrhu odkazem na sestavení, které obsahuje veřejné rozhraní a nastavením `Embed Interop Types` vlastnosti odkazu na. `True` To je ekvivalentní použití kompilátoru příkazového řádku a odkazování na sestavení pomocí `/link` možnosti kompilátoru. Klientský program pak může načíst instance objektů za běhu, které jsou zadány jako tato rozhraní. Pokud vytvoříte novou verzi sestavení modulu runtime se silným názvem, není nutné znovu kompilovat klientský program s aktualizovaným sestavením modulu runtime. Místo toho bude mít klientský program nadále k dispozici jakoukoli verzi sestavení modulu runtime s použitím vložených informací o typu pro veřejná rozhraní.

Vzhledem k tomu, že primární funkce vloženého typu je podpora vkládání informací o typu ze sestavení spolupracujících s objekty COM, platí při vložení informací o typu do plně spravovaného řešení následující omezení:

- Jsou vložené pouze atributy specifické pro zprostředkovatele komunikace s objekty COM. ostatní atributy se ignorují.

- Pokud typ používá obecné parametry a typ obecného parametru je vložený typ, tento typ nelze použít napříč hranicí sestavení. Příklady křížení hranice sestavení zahrnují volání metody z jiného sestavení nebo odvození typu z typu definovaného v jiném sestavení.

- Konstanty nejsou vloženy.

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Třída nepodporuje vložený typ jako klíč. Můžete implementovat vlastní typ slovníku pro podporu vloženého typu jako klíče.

V tomto návodu provedete následující akce:

- Vytvořte sestavení se silným názvem, které má veřejné rozhraní obsahující informace o typu, které mohou být vloženy.

- Vytvořte sestavení modulu runtime se silným názvem, které implementuje toto veřejné rozhraní.

- Vytvořte klientský program, který vloží informace o typu z veřejného rozhraní a vytvoří instanci třídy ze sestavení modulu runtime.

- Upravte a znovu sestavte sestavení modulu runtime.

- Spusťte klientský program, aby bylo vidět, že se nová verze sestavení modulu runtime používá, aniž by bylo nutné znovu kompilovat klientský program.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-an-interface"></a>Vytvoření rozhraní

#### <a name="to-create-the-type-equivalence-interface-project"></a>Vytvoření projektu rozhraní ekvivalenci typů

1. V aplikaci Visual Studio v nabídce **soubor** zvolte možnost **Nový** a poté klikněte na možnost **projekt**.

2. V dialogovém okně **Nový projekt** v podokně **typy projektů** se ujistěte, že je vybrána možnost **Windows** . V podokně **šablony** vyberte **Knihovna tříd** . Do pole **název** zadejte `TypeEquivalenceInterface`a pak klikněte na **OK**. Vytvoří se nový projekt.

3. V **Průzkumník řešení**klikněte pravým tlačítkem na soubor Class1.cs a klikněte na **Přejmenovat**. Přejmenujte soubor `ISampleInterface.cs` na a stiskněte klávesu ENTER. Přejmenováním souboru dojde také k přejmenování třídy na `ISampleInterface`. Tato třída bude představovat veřejné rozhraní pro třídu.

4. Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na **vlastnosti**. Klikněte na kartu **sestavení** . Nastavte výstupní cestu na platné umístění ve vývojovém počítači, například `C:\TypeEquivalenceSample`. Toto umístění bude také použito v pozdějším kroku tohoto návodu.

5. I když stále upravujete vlastnosti projektu, klikněte na kartu **podepisování** . Vyberte možnost **podepsat sestavení** . V seznamu **Vyberte soubor klíče se silným názvem** klikněte na  **\<nový... >** . Do pole **název souboru klíče** zadejte `key.snk`. Zrušte zaškrtnutí políčka **chránit soubor klíče heslem** . Klikněte na **OK**.

6. Otevřete soubor ISampleInterface.cs. Přidejte následující kód do souboru třídy ISampleInterface a vytvořte tak rozhraní ISampleInterface.

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

7. V nabídce **nástroje** klikněte na příkaz **vytvořit identifikátor GUID**. V dialogovém okně **vytvořit GUID** klikněte na **Formát registru** a pak klikněte na **Kopírovat**. Klikněte na tlačítko **ukončovací**.

8. V atributu odstraňte ukázkový identifikátor GUID a vložte ho do identifikátoru GUID, který jste zkopírovali v dialogovém okně **vytvořit GUID.** `Guid` Odeberte složené závorky ({}) ze zkopírovaného identifikátoru GUID.

9. V **Průzkumník řešení**rozbalte složku **Properties (vlastnosti** ). Dvakrát klikněte na soubor AssemblyInfo.cs. Do souboru přidejte následující atribut.

    ```csharp
    [assembly: ImportedFromTypeLib("")]
    ```

     Uložte soubor.

10. Uložte projekt.

11. Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na **sestavit**. Soubor Library. dll knihovny tříd je zkompilován a uložen do zadané výstupní cesty sestavení (například C:\TypeEquivalenceSample).

## <a name="creating-a-runtime-class"></a>Vytvoření běhové třídy

#### <a name="to-create-the-type-equivalence-runtime-project"></a>Vytvoření projektu pro ekvivalenty typu za běhu

1. V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.

2. V dialogovém okně **Nový projekt** v podokně **typy projektů** se ujistěte, že je vybrána možnost **Windows** . V podokně **šablony** vyberte **Knihovna tříd** . Do pole **název** zadejte `TypeEquivalenceRuntime`a pak klikněte na **OK**. Vytvoří se nový projekt.

3. V **Průzkumník řešení**klikněte pravým tlačítkem na soubor Class1.cs a klikněte na **Přejmenovat**. Přejmenujte soubor `SampleClass.cs` na a stiskněte klávesu ENTER. Přejmenování souboru také přejmenuje třídu na `SampleClass`. Tato třída implementuje `ISampleInterface` rozhraní.

4. Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na **vlastnosti**. Klikněte na kartu **sestavení** . Nastavte cestu výstupu do stejného umístění, které jste použili v projektu TypeEquivalenceInterface, `C:\TypeEquivalenceSample`například.

5. I když stále upravujete vlastnosti projektu, klikněte na kartu **podepisování** . Vyberte možnost **podepsat sestavení** . V seznamu **Vyberte soubor klíče se silným názvem** klikněte na  **\<nový... >** . Do pole **název souboru klíče** zadejte `key.snk`. Zrušte zaškrtnutí políčka **chránit soubor klíče heslem** . Klikněte na **OK**.

6. Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na **Přidat odkaz**. Klikněte na kartu **Procházet** a přejděte do složky výstupní cesta. Vyberte soubor TypeEquivalenceInterface. dll a klikněte na tlačítko **OK**.

7. V **Průzkumník řešení**rozbalte složku **odkazy** . Vyberte odkaz na TypeEquivalenceInterface. V okno Vlastnosti odkazu TypeEquivalenceInterface nastavte vlastnost **specifická verze** na **hodnotu false**.

8. Přidejte následující kód do souboru třídy SampleClass a vytvořte tak třídu SampleClass.

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

9. Uložte projekt.

10. Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na **sestavit**. Soubor Library. dll knihovny tříd je zkompilován a uložen do zadané výstupní cesty sestavení (například C:\TypeEquivalenceSample).

## <a name="creating-a-client-project"></a>Vytvoření projektu klienta

#### <a name="to-create-the-type-equivalence-client-project"></a>Vytvoření projektu klienta ekvivalenci typu

1. V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.

2. V dialogovém okně **Nový projekt** v podokně **typy projektů** se ujistěte, že je vybrána možnost **Windows** . V podokně **šablony** vyberte **Konzolová aplikace** . Do pole **název** zadejte `TypeEquivalenceClient`a pak klikněte na **OK**. Vytvoří se nový projekt.

3. Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na **vlastnosti**. Klikněte na kartu **sestavení** . Nastavte cestu výstupu do stejného umístění, které jste použili v projektu TypeEquivalenceInterface, `C:\TypeEquivalenceSample`například.

4. Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na **Přidat odkaz**. Klikněte na kartu **Procházet** a přejděte do složky výstupní cesta. Vyberte soubor TypeEquivalenceInterface. dll (ne TypeEquivalenceRuntime. dll) a klikněte na tlačítko **OK**.

5. V **Průzkumník řešení**rozbalte složku **odkazy** . Vyberte odkaz na TypeEquivalenceInterface. V okno Vlastnosti odkazu TypeEquivalenceInterface nastavte vlastnost **Embed Interop Types** na **hodnotu true**.

6. Do souboru Program.cs přidejte následující kód, který vytvoří klientský program.

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

7. Stisknutím kombinace kláves CTRL + F5 Sestavte a spusťte program.

## <a name="modifying-the-interface"></a>Změna rozhraní

#### <a name="to-modify-the-interface"></a>Změna rozhraní

1. V aplikaci Visual Studio v nabídce **soubor** přejděte na **otevřít**a potom klikněte na **projekt/řešení**.

2. V dialogovém okně **Otevřít projekt** klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a pak klikněte na **vlastnosti**. Klikněte na kartu **aplikace** . Klikněte na tlačítko **informace o sestavení** . Změňte **verze sestavení** a hodnoty **verze souboru** na `2.0.0.0`.

3. Otevřete soubor SampleInterface.cs. Do rozhraní ISampleInterface přidejte následující řádek kódu.

    ```csharp
    DateTime GetDate();
    ```

    Uložte soubor.

4. Uložte projekt.

5. Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na **sestavit**. Nová verze souboru Library. dll je zkompilována a uložena do zadané výstupní cesty sestavení (například C:\TypeEquivalenceSample).

## <a name="modifying-the-runtime-class"></a>Úprava běhové třídy

#### <a name="to-modify-the-runtime-class"></a>Úprava běhové třídy

1. V aplikaci Visual Studio v nabídce **soubor** přejděte na **otevřít**a potom klikněte na **projekt/řešení**.

2. V dialogovém okně **Otevřít projekt** klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na **vlastnosti**. Klikněte na kartu **aplikace** . Klikněte na tlačítko **informace o sestavení** . Změňte **verze sestavení** a hodnoty **verze souboru** na `2.0.0.0`.

3. Otevřete soubor SampleClass.cs. Do třídy SampleClass přidejte následující řádky kódu.

    ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
    ```

    Uložte soubor.

4. Uložte projekt.

5. Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na **sestavit**. Aktualizovaná verze souboru Library. dll je zkompilována a uložena v dříve zadané výstupní cestě sestavení (například C:\TypeEquivalenceSample).

6. V Průzkumníku souborů otevřete složku výstupní cesta (například C:\TypeEquivalenceSample). Dvakrát klikněte na TypeEquivalenceClient. exe a program spusťte. Program bude odrážet novou verzi TypeEquivalenceRuntime sestavení, aniž by byla znovu zkompilována.

## <a name="see-also"></a>Viz také:

- [/Link (C# možnosti kompilátoru)](../../../language-reference/compiler-options/link-compiler-option.md)
- [Průvodce programováním v jazyce C#](../../index.md)
- [Programování se sestaveními](../../../../framework/app-domains/programming-with-assemblies.md)
- [Sestavení v .NET](../../../../standard/assembly/index.md)
