---
title: Testování .NET Standard knihovny tříd pomocí .NET Core v Visual Studio Code
description: Vytvoří projekt testu jednotek pro knihovnu tříd .NET Core. Ověřte, zda knihovna tříd .NET Core pracuje správně s testy jednotek.
ms.date: 05/29/2020
ms.openlocfilehash: be227453bd441028cc6ce348c00fad944140238f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292187"
---
# <a name="tutorial-test-a-net-standard-library-with-net-core-in-visual-studio-code"></a>Kurz: testování knihovny .NET Standard pomocí .NET Core v Visual Studio Code

V tomto kurzu se dozvíte, jak automatizovat testování částí přidáním testovacího projektu do řešení.

## <a name="prerequisites"></a>Požadavky

- Tento kurz spolupracuje s řešením, které vytvoříte v části [Vytvoření knihovny .NET Standard v Visual Studio Code](library-with-visual-studio-code.md).

## <a name="create-a-unit-test-project"></a>Vytvoření projektu testování částí

1. Otevřete Visual Studio Code.

1. Otevřete `ClassLibraryProjects` řešení, které jste vytvořili v části [vytvoření knihovny .NET Standard v aplikaci Visual Studio](library-with-visual-studio.md).

1. Vytvořte projekt testu jednotek s názvem "StringLibraryTest".

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   Šablona projektu vytvoří soubor UnitTest1.cs s následujícím kódem:

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   Zdrojový kód vytvořený šablonou testu jednotky provede následující akce:

   - Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> obor názvů, který obsahuje typy používané pro testování částí.
   - Aplikuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atribut na `UnitTest1` třídu.
   - Použije <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut k definování `TestMethod1` .

   Každá metoda označená pomocí [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) v testovací třídě s označením [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) je provedena automaticky při spuštění testu jednotky.

   > [!NOTE]
   > MSTest je jedna ze tří testovacích rozhraní, ze kterých si můžete vybrat. Ostatní jsou xUnit a nUnit.

1. Přidejte testovací projekt do řešení.

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

1. Vytvořte odkaz na projekt knihovny tříd spuštěním následujícího příkazu:

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a>Přidat a spustit metody testování částí

Když aplikace Visual Studio spustí test jednotky, provede každou metodu, která je označena <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributem ve třídě, která je označena <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atributem. Testovací metoda končí při nalezení prvního selhání nebo po úspěšném dokončení všech testů obsažených v metodě.

Nejběžnější testy volají členy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> třídy. Mnoho metod Assert zahrnuje nejméně dva parametry, jeden z nich je očekávaný výsledek testu a druhý z nich je skutečný výsledek testu. `Assert`V následující tabulce jsou uvedeny některé často volané metody třídy:

| Metody Assert     | Funkce |
| ------------------ | -------- |
| `Assert.AreEqual`  | Ověřuje, zda jsou dvě hodnoty nebo objekty stejné. Vyhodnocení se nezdařila, pokud se hodnoty nebo objekty neshodují. |
| `Assert.AreSame`   | Ověřuje, že dvě proměnné objektu odkazují na stejný objekt. Pokud proměnné odkazují na různé objekty, vyhodnocení se nezdařilo. |
| `Assert.IsFalse`   | Ověřuje, jestli je podmínka `false` . Pokud je podmínka, vyhodnocení se nezdařilo `true` . |
| `Assert.IsNotNull` | Ověřuje, že objekt není `null` . Pokud je objekt, vyhodnocení se nezdařilo `null` . |

Můžete také použít <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> metodu v testovací metodě k označení typu výjimky, kterou očekává, že má být vyvolána. Test se nezdařil, pokud není vyvolána zadaná výjimka.

Při testování `StringLibrary.StartsWithUpper` metody je třeba zadat počet řetězců, které začínají velkým znakem. Očekáváte, že se metoda vrátí `true` v těchto případech, takže můžete volat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> metodu. Podobně je vhodné zadat počet řetězců, které začínají jinou výjimkou znaku velkého písmene. Očekáváte, že se metoda vrátí `false` v těchto případech, takže můžete volat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> metodu.

Vzhledem k tomu, že vaše metoda knihovny zpracovává řetězce, je také vhodné se ujistit, že úspěšně zpracovává [prázdný řetězec ( `String.Empty` )](xref:System.String.Empty) a a `null` řetězec. Prázdný řetězec je jeden, který nemá žádné znaky a jehož hodnota <xref:System.String.Length> je 0. `null`Řetězec je ten, který se neinicializoval. Můžete zavolat `StartsWithUpper` přímo jako statickou metodu a předat jeden <xref:System.String> argument. Nebo můžete zavolat `StartsWithUpper` jako metodu rozšíření pro `string` proměnnou přiřazenou k `null` .

Budete definovat tři metody, z nichž každá volá <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodu opakovaně pro každý prvek v poli řetězců. Vzhledem k tomu, že testovací metoda selže, jakmile najde první selhání, zavoláte přetížení metody, které vám umožní předat řetězec, který označuje hodnotu řetězce použitou ve volání metody.

Postup vytvoření testovacích metod:

1. Otevřete *StringLibraryTest/UnitTest1. cs* a nahraďte celý kód následujícím kódem.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   Test velkých písmen v `TestStartsWithUpper` metodě obsahuje řecké velké písmeno alfa (u + 0391) a velké písmeno cyrilice em (u + 041C). Test malých písmen v `TestDoesNotStartWithUpper` metodě obsahuje řecké malé písmeno alfa (U + 03B1) a malé písmeno g (u + 0433).

1. Uložte provedené změny.

1. Spusťte testy:

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   Výstup terminálu ukazuje, že všechny testy byly úspěšné.

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.

   Test Run Successful.
   Total tests: 3
        Passed: 3
   Total time: 5.1116 Seconds
   ```

## <a name="handle-test-failures"></a>Zpracování selhání testu

Pokud pracujete s vývojem řízeným testováním (TDD), napíšete nejprve testy a při jejich prvním spuštění dojde k chybě. Potom do aplikace přidáte kód, který provede test úspěšně. V tomto případě jste po zápisu kódu aplikace, který ověřuje, vytvořili test, takže jste neviděli test neúspěšný. Chcete-li ověřit, že test selže, pokud očekáváte, že selže, přidejte do vstupu testu neplatnou hodnotu.

1. Upravte `words` pole v `TestDoesNotStartWithUpper` metodě tak, aby obsahovalo řetězec "Error" (chyba).

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. Spusťte testy:

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   Výstup terminálu ukazuje, že jeden test se nezdařil, a obsahuje chybovou zprávu pro neúspěšný test.

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.
     X TestDoesNotStartWithUpper [283ms]
     Error Message:
      Assert.IsFalse failed. Expected for 'Error': false; Actual: True
     Stack Trace:
     at StringLibraryTest.UnitTest1.TestDoesNotStartWithUpper()
       in C:\Projects\ClassLibraryProjects\StringLibraryTest\UnitTest1.cs:line 33

   Test Run Failed.
   Total tests: 3
        Passed: 2
        Failed: 1
   Total time: 1.7825 Seconds
   ```

1. Vraťte změny, které jste provedli v kroku 1, a odeberte řetězec "Error" (chyba). Spusťte test znovu a testy proběhnou znovu.

## <a name="test-the-release-version-of-the-library"></a>Testování verze pro vydání knihovny

Nyní, když testy prošly všechny při spuštění ladicí verze knihovny, spusťte testy dodatečně k sestavení vydání knihovny. Několik faktorů, včetně optimalizací kompilátoru, může někdy způsobit různé chování mezi sestaveními ladění a vydání.

1. Spusťte testy s konfigurací sestavení vydaných verzí:

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   Testy jsou passované.

## <a name="additional-resources"></a>Další zdroje

- [Testování částí v .NET Core a .NET Standard](../testing/index.md)

## <a name="next-steps"></a>Další kroky

V tomto kurzu testujete jednotku knihovny tříd. Knihovnu můžete zpřístupnit ostatním tím, že ji publikujete do [NuGet](https://nuget.org) jako balíček. Pokud se chcete dozvědět, jak postupovat, postupujte podle kurzu NuGet:

> [!div class="nextstepaction"]
> [Vytvoření a publikování balíčku pomocí rozhraní příkazového řádku dotnet](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

Pokud knihovnu publikujete jako balíček NuGet, můžou ji nainstalovat a používat i ostatní. Pokud se chcete dozvědět, jak postupovat, postupujte podle kurzu NuGet:

> [!div class="nextstepaction"]
> [Instalace a použití balíčku pomocí rozhraní příkazového řádku dotnet](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

Knihovna nemusí být distribuována jako balíček. Dá se seskupit pomocí konzolové aplikace, která ho používá. Informace o tom, jak publikovat konzolovou aplikaci, najdete v předchozím kurzu v této sérii:

> [!div class="nextstepaction"]
> [Publikování konzolové aplikace .NET Core pomocí Visual Studio Code](publishing-with-visual-studio-code.md)
