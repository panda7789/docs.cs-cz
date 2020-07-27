---
title: Vytváření satelitních sestavení pro aplikace klasické pracovní plochy
description: Začněte vytvářet satelitní sestavení pro aplikace klasické pracovní plochy. Satelitní sestavení může být snadno Aktualizováno nebo nahrazeno k poskytnutí lokalizovaných prostředků.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- public keys, obtaining
- satellite assemblies
- assemblies [.NET Framework], signing
- application resources, deploying
- Al.exe
- GAC (global assembly cache), satellite assemblies
- Assembly Linker
- directory locations for satellite assemblies
- global assembly cache, satellite assemblies
- packaging application resources
- compiling satellite assemblies
- re-signing assemblies
ms.assetid: 8d5c6044-2919-41d2-8321-274706b295ac
ms.openlocfilehash: be6603f3a593d9756d55204024214660b2220af3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166218"
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a>Vytváření satelitních sestavení pro aplikace klasické pracovní plochy

Soubory prostředků hrají ústřední roli v lokalizovaných aplikacích. Umožňují aplikaci zobrazovat řetězce, obrázky a další data v jazyce a jazykové verzi uživatele a poskytovat alternativní data v případě, že prostředky pro vlastní jazyk nebo jazykovou verzi uživatele nejsou k dispozici. .NET Framework používá model hvězdicové a hvězdicové k vyhledání a načtení lokalizovaných prostředků. Centrum je hlavní sestavení, které obsahuje nelokalizovatelný spustitelný kód a prostředky pro jednu jazykovou verzi, která se nazývá neutrální nebo výchozí jazyková verze. Výchozí jazyková verze je záložní jazyková verze pro aplikaci. používá se, když nejsou k dispozici žádné lokalizované prostředky. Použijte <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut k určení jazykové verze výchozí jazykové verze aplikace. Každý paprsek se připojuje k satelitnímu sestavení, které obsahuje prostředky pro jednu lokalizovanou jazykovou verzi, ale neobsahuje žádný kód. Vzhledem k tomu, že satelitní sestavení nejsou součástí hlavního sestavení, můžete snadno aktualizovat nebo nahradit prostředky, které odpovídají konkrétní jazykové verzi, aniž by bylo nutné nahradit hlavní sestavení pro aplikaci.

> [!NOTE]
> Prostředky výchozí jazykové verze aplikace mohou být také uloženy v satelitním sestavení. K tomu přiřadíte <xref:System.Resources.NeutralResourcesLanguageAttribute> hodnotu atributu <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> .

## <a name="satellite-assembly-name-and-location"></a>Název a umístění satelitního sestavení

Model hvězdicové lokality vyžaduje umístění prostředků do konkrétních umístění, aby je bylo možné snadno vyhledat a použít. Pokud nezkompilujete a pojmenujte prostředky podle očekávání nebo pokud je neumístíte do správných umístění, modul CLR (Common Language Runtime) je nebude moci vyhledat a bude místo toho používat prostředky výchozí jazykové verze. .NET Framework Správce prostředků reprezentované <xref:System.Resources.ResourceManager> objektem, slouží k automatickému přístupu k lokalizovaným prostředkům. Správce prostředků vyžaduje následující:

- Jedno satelitní sestavení musí zahrnovat všechny prostředky pro konkrétní jazykovou verzi. Jinými slovy, je třeba zkompilovat více souborů *. txt* nebo *. resx* do jednoho binárního souboru *. Resources* .

- V adresáři aplikace musí být samostatný podadresář pro každou lokalizovanou jazykovou verzi, která ukládá prostředky této jazykové verze. Název podadresáře musí být stejný jako název jazykové verze. Alternativně můžete uložit satelitní sestavení do globální mezipaměti sestavení (GAC). V tomto případě musí součást informací o jazykové verzi silného názvu sestavení uvádět svou jazykovou verzi. (Další informace najdete v části [instalace satelitních sestavení v globální mezipaměti sestavení (GAC](#SN) ) dále v tomto tématu.)

  > [!NOTE]
  > Pokud vaše aplikace obsahuje prostředky pro subjazykové verze, umístěte každou podjazykovou verzi do samostatného podadresáře v adresáři aplikace. Neumísťujte subjazykové verze v podadresářích do adresáře hlavní jazykové verze.

- Satelitní sestavení musí mít stejný název jako aplikace a musí používat příponu názvu souboru .resources.dll. Například pokud má aplikace název *Example.exe*, musí být název každého satelitního sestavení *Example.resources.dll*. Všimněte si, že název satelitního sestavení neoznačuje jazykovou verzi svých souborů prostředků. Satelitní sestavení se však zobrazí v adresáři, který určuje jazykovou verzi.

- Informace o jazykové verzi satelitního sestavení musí být zahrnuty v metadatech sestavení. Chcete-li uložit název jazykové verze v metadatech satelitního sestavení, zadáte `/culture` možnost při použití [linkeru sestavení](../tools/al-exe-assembly-linker.md) pro vložení prostředků do satelitního sestavení.

Následující ilustrace znázorňuje ukázkovou adresářovou strukturu a požadavky na umístění pro aplikace, které neinstalujete do [globální mezipaměti sestavení (GAC](../app-domains/gac.md)). Položky s příponami. txt a. Resources nebudou dodávány s konečnou aplikací. Jedná se o mezilehlé soubory prostředků, které slouží k vytváření finálních sestavení satelitních prostředků. V tomto příkladu můžete nahradit soubory. resx pro soubory. txt. Další informace najdete v tématu [balení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md).

Následující obrázek ukazuje adresář satelitního sestavení:

![Adresář satelitního sestavení s lokalizovanými podadresáři kultur.](./media/creating-satellite-assemblies-for-desktop-apps/satellite-assembly-directory.gif)

## <a name="compiling-satellite-assemblies"></a>Kompilování satelitních sestavení

K kompilování textových souborů nebo souborů XML (*. resx*), které obsahují prostředky do binárních souborů *. Resources* , slouží [generátor souboru prostředků (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) . Pak použijete [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) k zkompilování souborů *. Resources* do satelitních sestavení. *Al.exe* vytvoří sestavení ze souborů *. Resources* , které zadáte. Satelitní sestavení mohou obsahovat pouze prostředky; nemohou obsahovat žádný spustitelný kód.

Následující *Al.exe* příkaz vytvoří satelitní sestavení pro aplikaci `Example` z německých souborů řetězců Resources *. de. Resources*.

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll
```

Následující příkaz *Al.exe* také vytvoří satelitní sestavení pro aplikaci `Example` ze souborů *strings. de. Resources*. Možnost **/template** způsobí, že satelitní sestavení zdědí všechna metadata sestavení s výjimkou jeho informací o jazykové verzi z nadřazeného sestavení (*Example.dll*).

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll
```  
  
V následující tabulce jsou popsány možnosti *Al.exe* používané v těchto příkazech podrobněji:
  
|Možnost|Popis|
|------------|-----------------|
|`-target:lib`|Určuje, že satelitní sestavení je zkompilováno do souboru knihovny (. dll). Vzhledem k tomu, že satelitní sestavení neobsahuje spustitelný kód a není hlavním sestavením aplikace, je nutné uložit satelitní sestavení jako knihovny DLL.|
|`-embed:strings.de.resources`|Určuje název souboru prostředků, který se má vložit, když *Al.exe* zkompiluje sestavení. Do satelitního sestavení můžete vložit více souborů. Resources, ale pokud používáte model hvězdicového a hvězdicového modelu, je nutné pro každou jazykovou verzi zkompilovat jedno satelitní sestavení. Můžete však vytvořit samostatné soubory. Resources pro řetězce a objekty.|
|`-culture:de`|Určuje jazykovou verzi prostředku, který má být zkompilován. Modul CLR (Common Language Runtime) používá tyto informace při hledání prostředků pro zadanou jazykovou verzi. Pokud tuto možnost vynecháte, bude *Al.exe* stále kompilovat prostředek, ale modul runtime ho nebude moci najít, když si ho uživatel požádá.|
|`-out:Example.resources.dll`|Určuje název výstupního souboru. Název musí následovat po názvech standard *Base*. Resources. *přípona*, kde je *základem* název hlavního sestavení a *přípona* je platná přípona názvu souboru (například. dll). Všimněte si, že modul runtime nemůže určit jazykovou verzi satelitního sestavení na základě názvu jeho výstupního souboru; k určení je nutné použít možnost **/culture** .|
|`-template:Example.dll`|Určuje sestavení, ze kterého bude satelitní sestavení dědit všechna metadata sestavení kromě pole culture. Tato možnost ovlivňuje satelitní sestavení pouze v případě, že zadáte sestavení se [silným názvem](../../standard/assembly/strong-named.md).|
  
 Úplný seznam možností, které jsou k dispozici v *Al.exe*, naleznete v tématu [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).
  
## <a name="satellite-assemblies-an-example"></a>Satelitní sestavení: příklad

Následuje jednoduchý příklad "Hello World", který zobrazuje okno se zprávou obsahující lokalizovaný pozdrav. Příklad obsahuje prostředky pro angličtinu (USA), francouzština (Francie) a ruština (Rusko) a její záložní jazyková verze je angličtina. Chcete-li vytvořit příklad, postupujte následovně:
  
1. Vytvořte soubor prostředků s názvem *Greetings. resx* nebo *Greeting.txt* , který bude obsahovat prostředek pro výchozí jazykovou verzi. Uloží jeden řetězec s názvem, `HelloString` jehož hodnota je Hello World!. v tomto souboru.

2. Chcete-li označit, že angličtina (EN) je výchozí jazyková verze aplikace, přidejte následující <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atribut do souboru AssemblyInfo aplikace nebo do hlavního souboru zdrojového kódu, který bude zkompilován do hlavního sestavení aplikace.

    [!code-csharp[Conceptual.Resources.Locating#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
    [!code-vb[Conceptual.Resources.Locating#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3. Přidejte podporu pro další jazykové verze (EN-US, fr-FR a ru-RU) do aplikace následujícím způsobem:  
  
    - Pro podporu jazykové verze en-US nebo angličtiny (USA) vytvořte soubor prostředků s názvem *Greetings. en-US. resx* nebo *Greeting.en-US.txt*a uložte ho do něj s jedním řetězcem s názvem `HelloString` "Hi World!".
  
    - Pro podporu jazykové verze fr-FR nebo francouzštiny (Francie) vytvořte soubor prostředků s názvem *Greeting.fr-fr. resx* nebo *Greeting.fr-FR.txt*a uložte ho do něj s jediným řetězcem, `HelloString` jehož hodnota je "Salut tout Le Monde!".
  
    - Pro podporu jazykové verze ru-RU nebo ruštiny (Rusko) vytvořte soubor prostředků s názvem *Greeting.ru-ru. resx* nebo *Greeting.ru-RU.txt*a uložte ho do něj s jediným řetězcem s názvem `HelloString` "Всем привет!".
  
4. Použijte [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) ke kompilaci každého textového souboru nebo souboru prostředků XML do binárního souboru *. Resources* . Výstupem je sada souborů, které mají stejný název kořenového souboru jako soubory *. resx* nebo *. txt* , ale rozšíření *. Resources* . Pokud vytvoříte příklad se sadou Visual Studio, proces kompilace se zpracuje automaticky. Pokud nepoužíváte aplikaci Visual Studio, spusťte následující příkazy pro zkompilování souborů *. resx* do souborů *. Resources* :  
  
    ```console
    resgen Greeting.resx
    resgen Greeting.en-us.resx
    resgen Greeting.fr-FR.resx
    resgen Greeting.ru-RU.resx
    ```

    Pokud jsou vaše prostředky v textových souborech namísto souborů XML, nahraďte příponu *. resx* textem *. txt*.

5. Zkompilujte následující zdrojový kód spolu s prostředky pro výchozí jazykovou verzi do hlavního sestavení aplikace:

    > [!IMPORTANT]
    > Pokud používáte příkazový řádek místo sady Visual Studio k vytvoření příkladu, měli byste změnit volání <xref:System.Resources.ResourceManager> konstruktoru třídy na následující:`ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`

    [!code-csharp[Conceptual.Resources.Locating#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
    [!code-vb[Conceptual.Resources.Locating#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]

    Pokud je aplikace pojmenována jako příklad a kompilujete z příkazového řádku, příkaz pro kompilátor jazyka C# je:

    ```console
    csc Example.cs -res:Greeting.resources
    ```

    Odpovídající příkaz kompilátoru Visual Basic:

    ```console
    vbc Example.vb -res:Greeting.resources
    ```

6. Vytvořte podadresář v hlavním adresáři aplikace pro každou lokalizovanou jazykovou verzi, kterou aplikace podporuje. Měli byste vytvořit podadresář *en-US*, *fr-FR*a *ru-ru* . Visual Studio vytvoří tyto podadresáře automaticky v rámci procesu kompilace.

7. Do satelitních sestavení vložte jednotlivé soubory *. Resources* specifické pro jazykovou verzi a uložte je do příslušného adresáře. Příkaz k tomuto účelu pro každý soubor *. Resources* je:

    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll
    ```

     kde *culture* je název jazykové verze, jejíž prostředky obsahuje satelitní sestavení. Visual Studio zpracovává tento proces automaticky.

Pak můžete spustit příklad. Bude náhodně vydávat jednu z podporovaných kultur aktuální jazykové verzi a zobrazí lokalizovaný pozdrav.

<a name="SN"></a>

## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a>Instalace satelitních sestavení do globální mezipaměti sestavení (GAC)

Namísto instalace sestavení v podadresáři místní aplikace je můžete nainstalovat do globální mezipaměti sestavení (GAC). To je zvlášť užitečné, pokud máte knihovny tříd a sestavení prostředků knihovny tříd, které jsou používány více aplikacemi.
  
Instalace sestavení do globální mezipaměti sestavení vyžaduje, aby měly silné názvy. Sestavení se silným názvem jsou podepsaná s platnou dvojicí veřejného a privátního klíče. Obsahují informace o verzi, kterou modul runtime používá k určení sestavení, které se má použít pro splnění požadavku vazby. Další informace o silných názvech a verzích najdete v tématu [Správa verzí sestavení](../../standard/assembly/versioning.md). Další informace o silných názvech naleznete v tématu [sestavení se silným názvem](../../standard/assembly/strong-named.md).

Při vývoji aplikace je nepravděpodobné, že budete mít přístup k finálnímu páru veřejného a privátního klíče. Chcete-li nainstalovat satelitní sestavení v globální mezipaměti sestavení (GAC) a zajistit, že funguje podle očekávání, můžete použít techniku nazvanou zpožděné podepisování. Při zpoždění podepsání sestavení v okamžiku sestavení rezervujete místo v souboru pro podpis silného názvu. Vlastní podepisování je zpožděné až později, až bude dostupný poslední pár veřejného a privátního klíče. Další informace o zpožděném podepisování naleznete v tématu [Delay Signing Assembly](../../standard/assembly/delay-sign.md).

### <a name="obtaining-the-public-key"></a>Získání veřejného klíče

Chcete-li zpozdit podepsání sestavení, je nutné mít přístup k veřejnému klíči. Můžete buď získat skutečný veřejný klíč z organizace ve vaší společnosti, který provede případné podepisování, nebo vytvořit veřejný klíč pomocí [Nástroje pro silný název (Sn.exe)](../tools/sn-exe-strong-name-tool.md).

Následující *Sn.exe* příkaz vytvoří pár veřejného a privátního klíče testu. Možnost **– k** určuje, že *Sn.exe* by měl vytvořit nový pár klíčů a uložit ho do souboru s názvem *TestKeyPair. snk*.
  
```console
sn –k TestKeyPair.snk
```

Veřejný klíč můžete extrahovat ze souboru, který obsahuje pár testovacích klíčů. Následující příkaz extrahuje veřejný klíč z *TestKeyPair. snk* a uloží jej do *PublicKey. snk*:

```console
sn –p TestKeyPair.snk PublicKey.snk
```

### <a name="delay-signing-an-assembly"></a>Zpoždění podepsání sestavení

Po získání nebo vytvoření veřejného klíče použijete [linker sestavení (Al.exe)](../tools/al-exe-assembly-linker.md) pro zkompilování sestavení a zadáte zpožděné podepisování.

Následující *Al.exe* příkaz vytvoří satelitní sestavení se silným názvem pro aplikaci StringLibrary ze souboru *strings. ja. Resources* :

```console
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk
```

Možnost **-Delay +** určuje, že linker sestavení by měl zpozdit podepsání sestavení. Možnost **-keyfile** Určuje název souboru klíče, který obsahuje veřejný klíč, který se použije pro Zpožděné podepsání sestavení.

### <a name="re-signing-an-assembly"></a>Opětovné podepsání sestavení

Před nasazením aplikace je nutné znovu podepsat zpožděné satelitní sestavení se skutečným párem klíčů. To můžete provést pomocí *Sn.exe*.

Následující příkaz *Sn.exe* podepíše *StringLibrary.resources.dll* dvojici klíčů uloženou v souboru *RealKeyPair. snk*. Možnost **– R** určuje, že dříve podepsané nebo zpožděné podepsané sestavení má být znovu podepsáno.

```console
sn –R StringLibrary.resources.dll RealKeyPair.snk
```

### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a>Instalace satelitního sestavení do globální mezipaměti sestavení (GAC)

Pokud modul runtime vyhledává prostředky v záložním procesu prostředků, hledá nejprve [globální mezipaměť sestavení (GAC](../app-domains/gac.md) ). (Další informace najdete v části "proces záložního prostředku" v tématu [balení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md) .) Jakmile je satelitní sestavení podepsáno silným názvem, lze jej nainstalovat do globální mezipaměti sestavení [(GAC) pomocí nástroj Global Assembly Cache Tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).

Následující *Gacutil.exe* příkaz nainstaluje *StringLibrary.resources.dll** v globální mezipaměti sestavení (GAC):

```console
gacutil -i:StringLibrary.resources.dll
```

Možnost **/i** určuje, že *Gacutil.exe* by měl nainstalovat zadané sestavení do globální mezipaměti sestavení (GAC). Po instalaci satelitního sestavení v mezipaměti budou prostředky, které obsahuje, zpřístupněny všem aplikacím, které jsou navrženy pro použití satelitního sestavení.

### <a name="resources-in-the-global-assembly-cache-an-example"></a>Prostředky v globální mezipaměti sestavení (GAC): příklad

Následující příklad používá metodu v knihovně tříd .NET Framework k extrakci a vrácení lokalizovaného pozdravu ze souboru prostředků. Knihovna a její prostředky jsou registrovány v globální mezipaměti sestavení (GAC). Příklad obsahuje prostředky pro angličtinu (USA), francouzština (Francie), ruština (Rusko) a anglické kultury. Výchozí jazyková verze je angličtina; jeho prostředky jsou uloženy v hlavním sestavení. Příklad prvotního zpoždění podepíše knihovnu a její satelitní sestavení pomocí veřejného klíče a pak je znovu podepíše s párem veřejného a privátního klíče. Chcete-li vytvořit příklad, postupujte následovně:

1. Pokud nepoužíváte aplikaci Visual Studio, použijte následující příkaz se [silným názvem (Sn.exe)](../tools/sn-exe-strong-name-tool.md) a vytvořte dvojici veřejného a privátního klíče s názvem *ResKey. snk*:

    ```console
    sn –k ResKey.snk
    ```

    Pokud používáte sadu Visual Studio, použijte k vygenerování souboru klíče kartu **podepisování** v dialogovém okně **vlastnosti** projektu.

2. K vytvoření souboru veřejného klíče s názvem *PublicKey. snk*použijte následující příkaz [nástroje se silným názvem (Sn.exe)](../tools/sn-exe-strong-name-tool.md) :

    ```console
    sn –p ResKey.snk PublicKey.snk
    ```

3. Vytvořte soubor prostředků s názvem *strings. resx* , který bude obsahovat prostředek pro výchozí jazykovou verzi. Uložte jeden řetězec s názvem `Greeting` , jehož hodnota je "jak provést?" v tomto souboru.

4. Chcete-li označit, že "en" je výchozí jazykovou verzí aplikace, přidejte následující <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atribut do souboru AssemblyInfo aplikace nebo do hlavního souboru zdrojového kódu, který bude zkompilován do hlavního sestavení aplikace:

    [!code-csharp[Conceptual.Resources.Satellites#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
    [!code-vb[Conceptual.Resources.Satellites#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]

5. Přidejte podporu pro další jazykové verze (kultury en-US, fr-FR a ru-RU) do aplikace následujícím způsobem:

    - Chcete-li podporovat jazykovou verzi "en-US" nebo anglickou (USA), vytvořte soubor prostředků s názvem *strings. en-US. resx* nebo *Strings.en-US.txt*a uložte jej do něj jediným řetězcem, `Greeting` jehož hodnota je "Hello!".

    - Pro podporu jazykové verze fr-FR nebo francouzštiny (Francie) vytvořte soubor prostředků s názvem *strings.fr-fr. resx* nebo *Strings.fr-FR.txt* a uložte ho do něj s jedním řetězcem s názvem `Greeting` "šťastného jour!".

    - Pro podporu "ru-RU" nebo ruské jazykové verze (Rusko) vytvořte soubor prostředků s názvem *strings.ru-ru. resx* nebo *Strings.ru-RU.txt* a uložte do něj jediný řetězec s názvem, `Greeting` jehož hodnota je "привет!".

6. Použijte [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) ke kompilaci každého textového souboru nebo souboru prostředků XML do binárního souboru. Resources. Výstupem je sada souborů, které mají stejný název kořenového souboru jako soubory *. resx* nebo *. txt* , ale rozšíření *. Resources* . Pokud vytvoříte příklad se sadou Visual Studio, proces kompilace se zpracuje automaticky. Pokud nepoužíváte aplikaci Visual Studio, spusťte následující příkaz pro zkompilování souborů *. resx* do souborů *. Resources* :

    ```console
    resgen filename
    ```

    Kde *filename* je volitelná cesta, název souboru a Přípona souboru *. resx* nebo textového souboru.

7. Zkompilujte následující zdrojový kód pro *StringLibrary. vb* nebo *StringLibrary.cs* spolu s prostředky pro výchozí jazykovou verzi do zpožděně podepsaného sestavení knihovny s názvem *StringLibrary.dll*:

    > [!IMPORTANT]
    > Pokud používáte příkazový řádek místo sady Visual Studio k vytvoření příkladu, měli byste změnit volání <xref:System.Resources.ResourceManager> konstruktoru třídy na `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);` .

    [!code-csharp[Conceptual.Resources.Satellites#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
    [!code-vb[Conceptual.Resources.Satellites#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]

    Příkaz pro kompilátor jazyka C# je:

    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs
    ```

    Odpovídající příkaz kompilátoru Visual Basic:

    ```console
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb
    ```

8. Vytvořte podadresář v hlavním adresáři aplikace pro každou lokalizovanou jazykovou verzi, kterou aplikace podporuje. Měli byste vytvořit podadresář *en-US*, *fr-FR*a *ru-ru* . Visual Studio vytvoří tyto podadresáře automaticky v rámci procesu kompilace. Vzhledem k tomu, že všechna satelitní sestavení mají stejný název souboru, podadresáře se používají k ukládání jednotlivých satelitních sestavení specifických pro jazykovou verzi, dokud nejsou podepsány pomocí páru veřejného a privátního klíče.

9. Vložte jednotlivé soubory *prostředků* specifické pro jazykovou verzi do zpožděně podepsaných satelitních sestavení a uložte je do příslušného adresáře. Příkaz k tomuto účelu pro každý soubor *. Resources* je:

    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk
    ```

    kde *culture* je název jazykové verze. V tomto příkladu jsou názvy jazykové verze en-US, fr-FR a ru-RU.

10. Znovu podepište *StringLibrary.dll* pomocí [nástroje Strong Name (Sn.exe)](../tools/sn-exe-strong-name-tool.md) následujícím způsobem:

    ```console
    sn –R StringLibrary.dll RealKeyPair.snk
    ```

11. Znovu podepište jednotlivá satelitní sestavení. Chcete-li to provést, použijte [Nástroj silného názvu (Sn.exe)](../tools/sn-exe-strong-name-tool.md) následujícím způsobem pro každé satelitní sestavení:

    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk
    ```

12. Pomocí následujícího příkazu zaregistrujte *StringLibrary.dll* a každého ze svých satelitních sestavení v globální mezipaměti sestavení (GAC):

    ```console
    gacutil -i filename
    ```

    kde *filename* je název souboru, který se má zaregistrovat.

13. Pokud používáte aplikaci Visual Studio, vytvořte nový projekt **konzolové aplikace** s názvem `Example` , přidejte odkaz na *StringLibrary.dll* a následující zdrojový kód a zkompilujte.

    [!code-csharp[Conceptual.Resources.Satellites#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
    [!code-vb[Conceptual.Resources.Satellites#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]

    Pro zkompilování z příkazového řádku, použijte následující příkaz pro kompilátor jazyka C#:

    ```console
    csc Example.cs -r:StringLibrary.dll
    ```

    Příkazový řádek pro kompilátor Visual Basic:

    ```console
    vbc Example.vb -r:StringLibrary.dll
    ```

14. Spusťte *Example.exe*.

## <a name="see-also"></a>Viz také

- [Zabalení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md)
- [Zpoždění podepsání sestavení](../../standard/assembly/delay-sign.md)
- [Al.exe (linker sestavení)](../tools/al-exe-assembly-linker.md)
- [Sn.exe (Nástroj pro silný název)](../tools/sn-exe-strong-name-tool.md)
- [Gacutil.exe (nástroj Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md)
- [Prostředky v aplikacích klasické pracovní plochy](index.md)
