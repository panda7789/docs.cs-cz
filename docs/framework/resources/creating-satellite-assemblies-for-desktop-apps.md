---
title: Vytváření satelitních sestavení pro aplikace klasické pracovní plochy
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c308c7e16f106d00e5fd1b5ad820f8b330f4bbbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a>Vytváření satelitních sestavení pro aplikace klasické pracovní plochy
Soubory prostředků hrají roli centrální v lokalizovaných aplikací. Umožňují aplikace k zobrazení řetězce, obrázky a další data ve vlastních jazyce a jazykové verzi a zadejte alternativní dat, pokud nejsou k dispozici prostředky pro uživatele vlastní jazyk nebo jazykovou verzi. Rozhraní .NET Framework používá model střed a paprsek najít a načíst lokalizované prostředky. Rozbočovače je hlavní sestavení, které obsahuje nepřekládá spustitelného kódu a prostředků pro jednu jazykovou verzi, která se nazývá neutrální nebo výchozí jazykovou verzi. Představuje výchozí jazykovou verzi záložní jazykovou verzi pro aplikaci. používá se při žádné lokalizované prostředky jsou k dispozici. Můžete použít <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut a nastavit jazykovou verzi aplikace výchozí jazykovou verzi. Každý paprsek připojí k satelitní sestavení, které obsahuje prostředky pro jeden lokalizované jazykovou verzi, ale neobsahuje žádný kód. Protože satelitní sestavení nejsou součástí hlavní sestavení, můžete snadno aktualizovat nebo nahradit prostředky, které odpovídají konkrétní jazykové verze bez nahrazení hlavního sestavení pro aplikaci.  
  
> [!NOTE]
>  Prostředky aplikace výchozí jazykovou verzi je možné ukládat i v satelitní sestavení. Chcete-li to provést, přiřaďte <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut hodnotu <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.  
  
## <a name="satellite-assembly-name-and-location"></a>Satelitní sestavení název a umístění  
 Model střed a paprsek vyžaduje umístit prostředky v určitých umístění tak, aby bylo možné snadno umístěný a použít. Pokud provedete kompilace a název prostředky podle očekávání, nebo pokud není umístit na správné místo, modul common language runtime nebude možné je vyhledat a místo ní použije prostředků výchozí jazykovou verzi. Rozhraní .NET Framework Resource Manager reprezentována <xref:System.Resources.ResourceManager> objektu, se používá k automatickému přístupu k lokalizované prostředky. Resource Manager vyžaduje následující:  
  
-   Jedno satelitní sestavení musí zahrnovat všechny prostředky pro konkrétní jazykové verzi. Jinými slovy by měl kompilaci víc souborů s příponou TXT nebo RESX do souboru .resources jeden binární.  
  
-   V adresáři aplikace pro jednotlivé lokalizované jazykové verze, obsahující tuto jazykovou verzi prostředky musí být samostatné podadresáři. Název podadresáře musí být stejný jako název jazykové verze. Alternativně můžete uložit satelitní sestavení v globální mezipaměti sestavení. V takovém případě komponenta informace o jazykové verzi sestavení silným názvem musí označovat jeho jazykovou verzi. (Viz [instalaci satelitní sestavení v globální mezipaměti sestavení](#SN) později v tomto tématu.)  
  
    > [!NOTE]
    >  Pokud vaše aplikace obsahuje prostředky pro subkultury, umístěte každou subkulturu v samostatných podadresáře v adresáři aplikace. Neumísťujte subkultury v podadresářích adresáře jejich hlavní jazykové verze.  
  
-   Satelitní sestavení musí mít stejný název jako aplikace a musí používat příponu názvu souboru ". resources.dll". Například pokud Example.exe název aplikace, název každé satelitní sestavení by měl být Example.resources.dll. Všimněte si, že název sestavení satelitní neindikuje jazykovou verzi jeho souborů prostředků. Satelitní sestavení se však zobrazí v adresáři, který zadat jazykovou verzi.  
  
-   Informace o jazykové verzi satelitní sestavení musí být součástí metadat sestavení. K uložení název jazykové verze v metadatech satelitní sestavení, zadejte `/culture` možnost při použití [Linker sestavení](../../../docs/framework/tools/al-exe-assembly-linker.md) na prostředky v satelitní sestavení pro vložení.  
  
 Následující obrázek znázorňuje directory strukturu a umístění požadavky ukázkového pro aplikace, které nejsou instalace v [globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md). Položky s příponami .txt a .resources nebude dodávají spolu s posledním aplikace. Jedná se o zprostředkující prostředků soubory použít k vytvoření konečné satelitní sestavení prostředků. V tomto příkladu můžete nahradit soubory RESX soubory s příponou TXT. Další informace najdete v tématu [balení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  
  
 ![Satelitní sestavení](../../../docs/framework/resources/media/satelliteassemblydir.gif "satelliteassemblydir")  
Directory satelitní sestavení  
  
## <a name="compiling-satellite-assemblies"></a>Kompilování satelitních sestavení  
 Používáte [Generátor zdrojových souborů (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) zkompilovat textové soubory nebo soubory XML (RESX), které obsahují prostředky pro binární soubory RESOURCES. Pak použijete [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) kompilace soubory .resources do satelitní sestavení. Al.exe vytvoří sestavení z soubory .resources, které zadáte. Satelitní sestavení může obsahovat pouze prostředky; nemohou obsahovat žádný spustitelný kód.  
  
 Následující příkaz pro Al.exe vytvoří satelitní sestavení pro aplikaci `Example` ze souboru strings.de.resources německé prostředky.  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll  
```  
  
 Následující příkaz pro Al.exe také vytvoří satelitní sestavení pro aplikaci `Example` ze souboru strings.de.resources. **/Template** možnost způsobí, že satelitní sestavení dědí všechny metadata sestavení s výjimkou jeho informace o jazykové verzi z nadřazeného sestavení (Example.dll).  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll  
```  
  
 Následující tabulka popisuje možnosti Al.exe používané v těchto příkazech podrobněji.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**-target:** lib|Určuje, že satelitní sestavení kompiluje soubor knihovny (DLL.dll). Protože satelitní sestavení neobsahuje spustitelného kódu a není hlavní sestavení aplikace, je nutné uložit satelitní sestavení jako knihovny DLL.|  
|**-vložení:** strings.de.resources|Určuje název souboru prostředků pro vložení při Al.exe kompiluje sestavení. Můžete vložit více RESOURCES souborů v satelitní sestavení, ale pokud postupujete podle modelu střed a paprsek, je nutné kompilovat jedno satelitní sestavení pro každou jazykovou verzi. Můžete však vytvořit samostatné RESOURCES soubory pro řetězce a objekty.|  
|**-jazyková verze:** de|Určuje jazykovou verzi prostředku ke kompilaci. Modul CLR používá tyto informace při vyhledávání pro prostředky pro zadanou jazykovou verzi. Pokud tento parametr vynecháte, Al.exe stále zkompiluje prostředek, ale modul runtime nebude možné najít, když uživatel požaduje.|  
|**-out:** Example.resources.dll|Určuje název souboru výstupního souboru. Název musí splňovat standardní pojmenování *baseName*.resources. *rozšíření*, kde *baseName* je název hlavní sestavení a *rozšíření* je platná přípona názvu souboru název (například .dll). Všimněte si, že modul runtime není schopna určit jazykovou verzi na základě jeho názvu souboru výstup; satelitní sestavení je nutné použít **/culture** možnost k jeho zadání.|  
|**-šablony:** Example.dll|Určuje, ze kterého satelitní sestavení zdědí všechny metadata sestavení s výjimkou pole jazykovou verzi sestavení. Tato možnost ovlivní satelitní sestavení pouze v případě, že zadáte sestavení, který má [silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md).|  
  
 Úplný seznam možností, které jsou k dispozici s Al.exe, najdete v části [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
## <a name="satellite-assemblies-an-example"></a>Satelitní sestavení: Příklad  
 Zde je jednoduchý příklad "Hello, world", který se zobrazí okno obsahující lokalizované pozdrav. V příkladu obsahuje zdroje informací pro angličtinu (Spojené státy), francouzština (Francie) a ruskými jazykové verze, a její záložní jazykové verze je angličtina. Pokud chcete vytvořit v příkladu, postupujte takto:  
  
1.  Vytvořte soubor prostředků s názvem Greeting.resx nebo Greeting.txt tak, aby obsahovala prostředků pro výchozí jazykovou verzi. Uložte jeden řetězec s názvem `HelloString` jehož hodnota je "Hello, world!" v tomto souboru.  
  
2.  K označení, že angličtina (cs) je výchozí jazykovou verzi aplikace, přidejte následující <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atribut souboru AssemblyInfo aplikace nebo souboru hlavní zdrojového kódu, který se zkompiluje do hlavní sestavení aplikace.  
  
     [!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
     [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3.  Přidání podpory pro další jazykové verze (en US, fr-FR a ru-RU) do aplikace takto:  
  
    -   Pro podporu en US nebo jazykové verze Angličtina (Spojené státy), vytvořte soubor prostředků s názvem Greeting.en-US.resx nebo Greeting.en US.txt a uložte do něj jeden řetězec s názvem `HelloString` jehož hodnota je "Hi world!"  
  
    -   Pro podporu fr-FR nebo Francouzština (Francie) jazykovou verzi, vytvořte soubor prostředků s názvem Greeting.fr-FR.resx nebo Greeting.fr FR.txt a uložte do něj jeden řetězec s názvem `HelloString` jehož hodnota je "Salut včetně the World!"  
  
    -   Pro podporu ru-RU nebo ruskými jazykovou verzi, vytvořte soubor prostředků s názvem Greeting.ru-RU.resx nebo Greeting.ru RU.txt a uložte do něj jeden řetězec s názvem `HelloString` jehož hodnota je "Всем привет!"  
  
4.  Použití [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) zkompilovat každé textu nebo prostředku soubor XML do souboru .resources binární. Výstupem je sada souborů, které mají stejný název kořenové jako soubory RESX nebo .txt, ale .resources rozšíření. Pokud v příkladu vytvoříte pomocí sady Visual Studio, se automaticky zpracovává proces kompilace. Pokud nepoužíváte Visual Studio, spusťte následující příkazy pro kompilaci souborů RESX na soubory .resources:  
  
    ```console
    resgen Greeting.resx  
    resgen Greeting.en-us.resx  
    resgen Greeting.fr-FR.resx  
    resgen Greeting.ru-RU.resx  
    ```  
  
     Pokud vaše prostředky v textových souborů místo soubory XML, nahraďte RESX příponu .txt.  
  
5.  Zkompilujte následující zdrojový kód společně s prostředky pro výchozí jazykovou verzi do hlavní sestavení aplikace:  
  
    > [!IMPORTANT]
    >  Pokud používáte příkazového řádku místo sady Visual Studio k vytvoření v příkladu, měli byste je upravit volání <xref:System.Resources.ResourceManager> konstruktoru třídy pro následující: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`  
  
     [!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
     [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]  
  
     Pokud aplikace jmenuje například a jsou kompilace z příkazového řádku, je příkaz pro kompilátor jazyka C#:  
  
    ```console  
    csc Example.cs -res:Greeting.resources  
    ```  
  
     Příkaz odpovídající kompilátoru jazyka Visual Basic je:  
  
    ```console  
    vbc Example.vb -res:Greeting.resources  
    ```  
  
6.  Vytvořte podadresáře v adresáři hlavní aplikace pro jednotlivé lokalizované jazykové verze aplikací podporováno. Měli byste vytvořit en US, fr-FR a podadresáři ru-RU. Visual Studio vytvoří tyto podadresáře automaticky jako součást procesu kompilace.  
  
7.  Vložit soubory .resources jednotlivých specifické pro jazykovou verzi na satelitní sestavení a uložit je do příslušného adresáře. Příkaz k tomu pro každý soubor .resources je:  
  
    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll  
    ```  
  
     kde *jazykovou verzi* je název jazykové verze, jejíž prostředky satelitní sestavení obsahuje. Visual Studio zpracovává tento proces automaticky.  
  
 Potom můžete spustit v příkladu. Náhodně to bude dávat mezi podporovaném jazykových verzí aktuální jazykovou verzi a zobrazí lokalizované pozdrav.  
  
<a name="SN"></a>   
## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a>Instalace satelitní sestavení v globální mezipaměti sestavení  
 Místo instalace sestavení v podadresáři místní aplikace, můžete je nainstalovat v globální mezipaměti sestavení. To je zvlášť užitečné, pokud máte knihovny tříd a třída knihovna prostředků sestavení, které používají více aplikací.  
  
 Instalace sestavení do globální mezipaměti sestavení vyžaduje, aby měli silné názvy. Sestavení se silným názvem jsou podepsané platný pár veřejného a privátního klíče. Obsahují informace o verzi, která modul runtime používá k určení sestavení pro použití, které by vyhovovaly žádosti vazby. Další informace o silné názvy a verze najdete v tématu [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md). Další informace o silné názvy najdete v tématu [sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
 Při vývoji aplikace, není pravděpodobné, že budete mít přístup k posledním pár veřejného a privátního klíče. Abyste mohli nainstalovat satelitní sestavení v globální mezipaměti sestavení a ujistěte se, že funguje podle očekávání, můžete použít techniku zvanou zpožděné podepisování. Pokud jste zpoždění podepsání sestavení, v okamžiku sestavení můžete rezervovat místo v souboru pro podpis silného názvu. Podepisování je objevit až později, pokud není k dispozici poslední pár veřejného a privátního klíče. Další informace o zpožděné podepisování najdete v tématu [zpoždění podepsání sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="obtaining-the-public-key"></a>Získání veřejného klíče  
 Zpoždění podepsání sestavení, musí mít přístup k veřejný klíč. Buď můžete získat reálný veřejný klíč z organizace ve vaší společnosti, který bude případné podepsání nebo vytvořit veřejný klíč pomocí [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  
  
 Následující příkaz pro Sn.exe vytvoří testovací dvojici veřejného a privátního klíče. **– K** možnost určuje, že by měl vytvořit nový pár klíčů a uložit ho do souboru s názvem TestKeyPair.snk Sn.exe.  
  
```console
sn –k TestKeyPair.snk   
```  
  
 Veřejný klíč lze extrahovat ze souboru, který obsahuje pár klíčů testu. Následující příkaz extrahuje veřejný klíč z TestKeyPair.snk a uloží ho do PublicKey.snk:  
  
```console
sn –p TestKeyPair.snk PublicKey.snk  
```  
  
### <a name="delay-signing-an-assembly"></a>Zpoždění podepsání sestavení  
 Když Získejte nebo vytvořte veřejný klíč, můžete použít [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) pro kompilaci sestavení a určení odložené podepisování.  
  
 Následující příkaz pro Al.exe vytvoří silným názvem satelitní sestavení pro aplikaci StringLibrary ze souboru strings.ja.resources:  
  
```console 
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk  
```  
  
 **-Zpoždění +** možnost určuje, že by měl Linker sestavení zpoždění podepsání sestavení. **- Keyfile** možnost určuje název souboru klíče, který obsahuje veřejný klíč sloužící k zpoždění podepsání sestavení.  
  
### <a name="re-signing-an-assembly"></a>Znovu podepisování sestavení  
 Před nasazením aplikace, musíte znovu podepsat zpoždění podepsané satelitní sestavení s reálné dvojice klíčů. To provedete pomocí Sn.exe.  
  
 Následující příkaz pro Sn.exe podepisuje StringLibrary.resources.dll s pár klíčů, které jsou uložené v souboru RealKeyPair.snk. **– R** možnost určuje, že dříve podepsaný nebo zpoždění podepsané sestavení je znovu podepsat.  
  
```console
sn –R StringLibrary.resources.dll RealKeyPair.snk   
```  
  
### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a>Instalace satelitní sestavení v globální mezipaměti sestavení  
 Když modul runtime hledá prostředky v nouzové procesy prostředků, se hledá v [globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md) první. (Další informace najdete v části "Proces nouzového prostředku" [balení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) tématu.) Jakmile satelitní sestavení je podepsáno silným názvem, může být nainstalovat v globální mezipaměti sestavení pomocí [Global Assembly Cache Tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
 Následující příkaz pro Gacutil.exe nainstaluje StringLibrary.resources.dll v globální mezipaměti sestavení:  
  
```console
gacutil -i:StringLibrary.resources.dll  
```  
  
 **/I** možnost určuje, že Gacutil.exe nainstalovat zadané sestavení do globální mezipaměti sestavení. Po satelitní sestavení nainstalováno v mezipaměti, které obsahuje prostředky k dispozici pro všechny aplikace, které jsou určeny k použití satelitní sestavení.  
  
### <a name="resources-in-the-global-assembly-cache-an-example"></a>Prostředky v globální mezipaměti sestavení: příklad  
 Následující příklad používá metodu v knihovně tříd rozhraní .NET Framework extrahovat a vrátí lokalizované pozdravu ze zdrojového souboru. Knihovnu a její prostředky je zaregistrovaný v globální mezipaměti sestavení. V příkladu obsahuje zdroje informací pro angličtinu (Spojené státy), francouzština (Francie), ruština (Rusko) a anglické jazykové verze. Je angličtina výchozí jazykovou verzi; jeho prostředky jsou uloženy v hlavní sestavení. V příkladu zpoždění začátku přihlásí knihovnu a její satelitní sestavení s veřejným klíčem, pak znovu podepíše je pomocí pár veřejného a privátního klíče. Pokud chcete vytvořit v příkladu, postupujte takto:  
  
1.  Pokud nepoužíváte Visual Studio, použijte následující [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) příkaz pro vytvoření páru veřejného a privátního klíče RSA s názvem ResKey.snk:  
  
    ```console
    sn –k ResKey.snk  
    ```  
  
     Pokud používáte Visual Studio, použijte **podpisování** Karta projektu **vlastnosti** dialogové okno pro vytvoření souboru klíče.  
  
2.  Použijte následující [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) příkazu vytvořte soubor veřejného klíče s názvem PublicKey.snk:  
  
    ```console
    sn –p ResKey.snk PublicKey.snk  
    ```  
  
3.  Vytvořte soubor prostředků s názvem Strings.resx tak, aby obsahovala prostředků pro výchozí jazykovou verzi. Uložte jeden řetězec s názvem `Greeting` jehož hodnota je "Jak proveďte vám proveďte?" v tomto souboru.  
  
4.  K označení, že "en" je výchozí jazykovou verzi aplikace, přidejte následující <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atribut souboru AssemblyInfo aplikace nebo souboru hlavní zdrojového kódu, který se zkompiluje do hlavní sestavení aplikace:  
  
     [!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
     [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]  
  
5.  Přidáte podporu pro další jazykové verze (kultur en US, fr-FR a ru-RU) do aplikace takto:  
  
    -   Pro podporu "en US" nebo jazykové verze Angličtina (Spojené státy), vytvořte soubor prostředků s názvem Strings.en-US.resx nebo Strings.en US.txt a uložte do něj jeden řetězec s názvem `Greeting` jehož hodnota je "Hello!".  
  
    -   Pro podporu "fr-FR" nebo Francouzština (Francie) jazykovou verzi, vytvořte soubor prostředků s názvem Strings.fr-FR.resx nebo Strings.fr FR.txt a uložte do něj jeden řetězec s názvem `Greeting` jehož hodnota je "Pozvánka jour!"  
  
    -   Pro podporu "ru-RU" nebo ruskými jazykovou verzi, vytvořte soubor prostředků s názvem Strings.ru RU.resx nebo Strings.ru RU.txt a uložte do něj jeden řetězec s názvem `Greeting` jehož hodnota je "Привет!"  
  
6.  Použití [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) zkompilovat každé textu nebo prostředku soubor XML do souboru .resources binární. Výstupem je sada souborů, které mají stejný název kořenové jako soubory RESX nebo .txt, ale .resources rozšíření. Pokud v příkladu vytvoříte pomocí sady Visual Studio, se automaticky zpracovává proces kompilace. Pokud nepoužíváte Visual Studio, spusťte následující příkaz pro kompilaci souborů RESX na soubory .resources:  
  
    ```console
    resgen filename  
    ```  
  
     kde *filename* je volitelná cesta, název souboru a příponu souboru RESX nebo text.  
  
7.  Kompilace následující zdrojový kód pro StringLibrary.vb nebo StringLibrary.cs spolu s prostředky pro výchozí jazykovou verzi do zpoždění podepsané sestavení knihovny s názvem StringLibrary.dll:  
  
    > [!IMPORTANT]
    >  Pokud používáte příkazového řádku místo sady Visual Studio k vytvoření v příkladu, měli byste je upravit volání <xref:System.Resources.ResourceManager> konstruktoru třídy k `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.  
  
     [!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
     [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]  
  
     Příkaz pro kompilátor jazyka C# je:  
  
    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs  
    ```  
  
     Příkaz odpovídající kompilátoru jazyka Visual Basic je:  
  
    ```console  
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb  
    ```  
  
8.  Vytvořte podadresáře v adresáři hlavní aplikace pro jednotlivé lokalizované jazykové verze aplikací podporováno. Měli byste vytvořit en US, fr-FR a podadresáři ru-RU. Visual Studio vytvoří tyto podadresáře automaticky jako součást procesu kompilace. Vzhledem k tomu, že všechny satelitní sestavení se stejným názvem, podadresáře se používají k ukládání jednotlivých specifické pro jazykovou verzi satelitní sestavení, dokud jsou podepsané s pár veřejného a privátního klíče.  
  
9. Vložení jednotlivých soubory .resources specifické pro jazykovou verzi do zpoždění podepsané satelitní sestavení a uložit je do příslušného adresáře. Příkaz k tomu pro každý soubor .resources je:  
  
    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk  
    ```  
  
     kde *jazykovou verzi* je název jazykové verze. V tomto příkladu jsou názvy jazykové verze en US, fr-FR a ru-RU.  
  
10. Znovu podepsat pomocí StringLibrary.dll [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) následujícím způsobem:  
  
    ```console
    sn –R StringLibrary.dll RealKeyPair.snk  
    ```  
  
11. Znovu podepíšete jednotlivých satelitní sestavení. Chcete-li to provést, použijte [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) takto pro každé satelitní sestavení:  
  
    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk  
    ```  
  
12. Registrace StringLibrary.dll a každý z jeho satelitních sestavení v globální mezipaměti sestavení pomocí následujícího příkazu:  
  
    ```console
    gacutil -i filename  
    ```  
  
     kde *filename* je název souboru k registraci.  
  
13. Pokud používáte Visual Studio, vytvořte novou **konzolové aplikace** projektu s názvem `Example`do ní přidejte odkaz na StringLibrary.dll a následující zdrojový kód a zkompilovat.  
  
     [!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
     [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]  
  
     Kompilace z příkazového řádku, použijte následující příkaz pro kompilátor jazyka C#:  
  
    ```console
    csc Example.cs -r:StringLibrary.dll   
    ```  
  
     Příkazový řádek kompilátoru jazyka Visual Basic je:  
  
    ```console
    vbc Example.vb -r:StringLibrary.dll   
    ```  
  
14. Spusťte Example.exe.  
  
## <a name="see-also"></a>Viz také  
 [Zabalení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Zpoždění podepsání sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 [Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Sn.exe (nástroj pro silný název)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [Gacutil.exe (nástroj globální mezipaměti sestavení)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)
