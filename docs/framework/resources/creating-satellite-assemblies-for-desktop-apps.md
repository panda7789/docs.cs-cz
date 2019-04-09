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
ms.openlocfilehash: ff0e51ad0d0e12c944c996a4262541fb980efe05
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138005"
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a>Vytváření satelitních sestavení pro aplikace klasické pracovní plochy
Soubory prostředků přehrát hlavní roli v lokalizovaných aplikacích. Umožňují aplikaci zobrazíte řetězce, obrázky a další data v vlastněných uživateli jazyk a jazykovou verzi a poskytnout alternativní dat, pokud nejsou k dispozici prostředky pro uživatele vlastní jazyk nebo jazykovou verzi. Model střed a paprsek rozhraní .NET Framework používá k vyhledání a načtení lokalizovaných prostředků. Centrum je hlavní sestavení, která obsahuje spustitelný kód bez možnosti lokalizace a prostředky pro jediné jazykové verze, která se nazývá neutrální nebo výchozí jazykovou verzi. Výchozí jazykovou verzi je záložní jazykovou verzi pro aplikaci. používá se, když jsou k dispozici žádné lokalizované prostředky. Můžete použít <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut k určení jazykovou verzi aplikace výchozí jazykovou verzi. Každého paprsku se připojí k satelitní sestavení, která obsahuje prostředky pro jeden lokalizovanou jazykovou verzi, ale neobsahuje žádný kód. Protože satelitní sestavení nejsou součástí hlavní sestavení, můžete snadno aktualizovat nebo nahradit prostředky, které odpovídají konkrétní jazykovou verzi, bez nutnosti vyměnit hlavní sestavení pro aplikaci.  
  
> [!NOTE]
>  Prostředky aplikace výchozí jazykovou verzi mohou být uloženy také v satelitním sestavení. Chcete-li to provést, přiřaďte <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut hodnotu <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.  
  
## <a name="satellite-assembly-name-and-location"></a>Satelitní sestavení název a umístění  
 Model střed a paprsek vyžaduje umístit prostředky v konkrétní umístění tak, aby bylo možné snadno nachází a použít. Pokud tak učiníte kompilace a název prostředky podle očekávání nebo je umístit není ve správném umístění, modul common language runtime nebudete moct umisťovat a místo toho použije prostředků výchozí jazykové verze. Rozhraní .NET Framework Resource Manageru reprezentována <xref:System.Resources.ResourceManager> objektu, se používá k automatickému přístupu k lokalizované prostředky. Resource Manageru vyžaduje následující:  
  
-   Jedno satelitní sestavení musí zahrnovat všechny prostředky pro konkrétní jazykovou verzi. Jinými slovy byste měli kompilovat více souborů .txt nebo .resx do jediné binární soubor .resources.  
  
-   Musí být samostatné podadresář v adresáři aplikace pro každou lokalizovanou jazykovou verzi, která ukládá danou jazykovou verzi prostředků. Název podadresáře musí být stejný jako název jazykové verze. Alternativně můžete uložit satelitní sestavení v globální mezipaměti sestavení. V takovém případě součást informací o jazykové verzi sestavení silným názvem musíte uvést jeho jazykovou verzi. (Viz [instalace satelitní sestavení v globální mezipaměti sestavení](#SN) později v tomto tématu.)  
  
    > [!NOTE]
    >  Pokud vaše aplikace obsahuje prostředky pro subkultury, umístěte každou subkulturu v samostatném podadresáři adresáře aplikace. Neumísťujte subkultury v podadresářích adresáře jejich hlavní jazykové verze.  
  
-   Satelitní sestavení musí mít stejný název jako aplikace a musíte použít příponu názvu souboru ". resources.dll". Například pokud aplikace jmenuje Example.exe, název každé satelitní sestavení by měl být Example.resources.dll. Všimněte si, že název sestavení satelitních neznamená jazykovou verzi jeho souborů prostředků. Satelitní sestavení se však zobrazí do adresáře, který zadat jazykovou verzi.  
  
-   Informace o jazykové verzi satelitního sestavení musí obsahovat metadata sestavení. Chcete-li uložit název jazykové verze v metadatech satelitní sestavení, zadejte `/culture` možnost při použití [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md) pro vložení prostředkům v satelitním sestavení.  
  
 Následující obrázek znázorňuje ukázka directory struktuře a umístění požadavky pro aplikace, které nejsou instalace v [globální mezipaměti sestavení](../../../docs/framework/app-domains/gac.md). Položky s příponami TXT a .resources nebude dodání pomocí konečné aplikace. Jsou to soubory zprostředkující prostředek použitý k vytvoření konečného satelitní sestavení prostředků. V tomto příkladu můžete nahradit souborů .resx pro soubory TXT. Další informace najdete v tématu [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  
  
 ![Satelitní sestavení](../../../docs/framework/resources/media/satelliteassemblydir.gif "satelliteassemblydir")  
Adresář satelitního sestavení  
  
## <a name="compiling-satellite-assemblies"></a>Kompilování satelitních sestavení  
 Použijete [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) ke kompilaci textové soubory nebo soubory XML (.resx), které obsahují prostředky do binárních souborů .resources. Pak použijete [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) ke kompilaci souborů .resources do satelitních sestavení. Vytvoří Al.exe sestavení ze souborů .resources, které zadáte. Satelitní sestavení může obsahovat pouze prostředky; nesmí obsahovat žádný spustitelný kód.  
  
 Následující příkaz Al.exe vytvoří satelitní sestavení pro aplikaci `Example` ze souboru strings.de.resources německé prostředky.  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll  
```  
  
 Následující příkaz Al.exe také vytvoří satelitní sestavení pro aplikaci `Example` ze souboru strings.de.resources. **/Template** možnost způsobí, že satelitní sestavení dědí všechna metadata sestavení s výjimkou jeho informace o jazykové verzi z nadřazeného sestavení (Example.dll).  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll  
```  
  
 Následující tabulka popisuje možnosti Al.exe použité v příkazech podrobněji.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**-target:** lib|Určuje, že satelitní sestavení je kompilováno do souboru knihovny (DLL.dll). Protože satelitní sestavení neobsahuje žádná spustitelný kód a není sestavení hlavní aplikace, je nutné uložit jako knihovny DLL satelitních sestavení.|  
|**-embed:** strings.de.resources|Určuje název souboru prostředků pro vložení při Al.exe zkompiluje sestavení. Můžete vložit několik souborů .resources v satelitním sestavení, ale pokud postupujete model střed a paprsek, musíte zkompilovat jedno satelitní sestavení pro každou jazykovou verzi. Můžete však vytvořit oddělených souborů .resources pro řetězce a objekty.|  
|**-jazykové verze:** de|Určuje jazykovou verzi prostředků pro kompilaci. Modul common language runtime používá tyto informace při vyhledávání prostředků pro zadanou jazykovou verzi. Pokud tento parametr vynecháte, Al.exe se stále zkompiluje prostředek, ale modul runtime nebude možné najít, když uživatel požaduje.|  
|**-out:** Example.resources.dll|Určuje název výstupního souboru. Název musí splňovat standardní pojmenování *baseName*.resources. *rozšíření*, kde *baseName* je název hlavního sestavení a *rozšíření* je platnou příponu (například .dll). Všimněte si, že modul runtime nedokáže určit jazykovou verzi satelitního sestavení založené na jeho název výstupního souboru; je nutné použít **/culture** možnost k jeho zadání.|  
|**– Šablona:** Example.dll|Určuje sestavení, ze kterého se satelitní sestavení dědí všechna metadata sestavení s výjimkou pole jazykové verze. Tato možnost se týká satelitní sestavení pouze v případě, že při zadání sestavení, který má [silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md).|  
  
 Úplný seznam možností, které jsou s Al.exe najdete v tématu [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
## <a name="satellite-assemblies-an-example"></a>Satelitní sestavení: Příklad  
 Níže je jednoduchý příklad "Hello world", který se zobrazí okno se zprávou obsahující lokalizované pozdrav. V příkladu obsahuje prostředky pro angličtinu (Spojené státy), francouzština (Francie) a jazykové verze ruština (Rusko) a jeho záložní jazykovou verzi je angličtina. Chcete-li vytvořit příklad, postupujte takto:  
  
1.  Vytvoření souboru prostředků s názvem Greeting.resx nebo Greeting.txt tak, aby obsahovala prostředků pro výchozí jazykovou verzi. Jeden řetězec s názvem Store `HelloString` jehož hodnota je "Hello world!" v tomto souboru.  
  
2.  K označení, že je angličtina (en) výchozí jazykovou verzi aplikace, přidejte následující <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atribut souboru AssemblyInfo aplikace nebo souboru hlavní zdrojového kódu, který se zkompiluje do sestavení hlavní aplikace.  
  
     [!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
     [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3.  Přidání podpory pro další jazykové verze (en US, fr-FR a ru-RU) aplikace následujícím způsobem:  
  
    -   Pro podporu en US nebo jazykové verze Angličtina (Spojené státy), vytvořit soubor prostředků s názvem Greeting.en US.resx nebo Greeting.en US.txt a do ní uložte jednoho řetězce s názvem `HelloString` jehož hodnota je "Ahoj světe!"  
  
    -   Pro podporu fr-FR nebo jazykovou verzi francouzština (Francie), vytvořit soubor prostředků s názvem Greeting.fr-FR.resx nebo Greeting.fr FR.txt a do ní uložte jednoho řetězce s názvem `HelloString` jehož hodnota je "Salut včetně the World!"  
  
    -   Pro podporu, ru-RU nebo ruština (Rusko) jazykovou verzi, vytvořit soubor prostředků s názvem Greeting.ru RU.resx nebo Greeting.ru RU.txt a do ní uložte jednoho řetězce s názvem `HelloString` jehož hodnota je "Всем привет!"  
  
4.  Použití [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) kompilace jednotlivých textu nebo XML souboru prostředků do binárního souboru .resources. Výstupem je sada souborů, které mají stejný název kořenového souboru jako soubory RESX a txt, ale s příponou .resources. Pokud v příkladu vytvoříte pomocí sady Visual Studio, je automaticky zpracována proces kompilace. Pokud nepoužíváte Visual Studio, spusťte následující příkazy pro kompilaci souborů .resx na soubory .resources:  
  
    ```console
    resgen Greeting.resx  
    resgen Greeting.en-us.resx  
    resgen Greeting.fr-FR.resx  
    resgen Greeting.ru-RU.resx  
    ```  
  
     Pokud jsou vaše prostředky v textových souborech místo souborů XML, nahraďte příponou .resx .txt.  
  
5.  Zkompilujte následující kód zdroj spolu s prostředky pro výchozí jazykovou verzi do sestavení hlavní aplikace:  
  
    > [!IMPORTANT]
    >  Pokud používáte příkazového řádku namísto Visual Studio k vytvoření příkladu, byste měli upravit volání <xref:System.Resources.ResourceManager> konstruktoru třídy takto: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`  
  
     [!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
     [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]  
  
     Pokud aplikace jmenuje například a při kompilaci z příkazového řádku pro příkaz C# kompilátoru je:  
  
    ```console  
    csc Example.cs -res:Greeting.resources  
    ```  
  
     Příkaz odpovídající kompilátoru jazyka Visual Basic je:  
  
    ```console  
    vbc Example.vb -res:Greeting.resources  
    ```  
  
6.  Vytvořte podadresář v adresáři hlavní aplikace pro každou lokalizovanou jazykovou verzi podporováno v aplikaci. Měli byste vytvořit en US, fr-FR a podadresář ru-RU. Tyto podsložky Visual Studio automaticky vytvoří jako součást procesu kompilace.  
  
7.  Vložení souborů .resources jednotlivých specifické pro jazykovou verzi do satelitních sestavení a uložit je do příslušného adresáře. Příkaz pro každý soubor .resources je:  
  
    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll  
    ```  
  
     kde *jazykovou verzi* je název jazykové verze, jejíž prostředků obsahuje satelitní sestavení. Visual Studio automaticky zpracovává tento proces.  
  
 Potom můžete spustit v příkladu. Náhodně bude jeden z podporovaných jazykových verzí aktuální jazykové verze a zobrazit lokalizované pozdrav.  
  
<a name="SN"></a>   
## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a>Instalace satelitní sestavení v globální mezipaměti sestavení  
 Místo instalace sestavení v podadresáři místní aplikace, můžete je nainstalovat do globální mezipaměti sestavení. To je zvlášť užitečné, pokud máte sestavení prostředků knihovny tříd, které jsou používány více aplikací a knihoven tříd.  
  
 Instalace sestavení do globální mezipaměti sestavení vyžaduje, ke kterým mají silných názvů. Sestavení se silným názvem jsou podepsány pomocí platný dvojice veřejného/soukromého klíče. Obsahují informace o verzi, která modul runtime používá k určení sestavení, které by vyhovovaly žádosti o vazbu pomocí. Další informace o silné názvy a správy verzí, naleznete v tématu [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md). Další informace o silných názvů najdete v tématu [sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
 Když vyvíjíte aplikaci, je pravděpodobné, že budete mít přístup k poslední dvojice veřejného/soukromého klíče. Pokud chcete nainstalovat satelitní sestavení v globální mezipaměti sestavení a ujistěte se, že funguje podle očekávání, můžete použít techniky označované jako zpožděného podepisování. Pokud jste zpoždění podepsání sestavení, v okamžiku sestavení můžete rezervovat místo v souboru pro podpis silného názvu. Podepisování je zpožděna, dokud později, když je k dispozici konečná dvojice veřejného/soukromého klíče. Další informace o zpožděného podepisování naleznete v tématu [zpožděné podepisování sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="obtaining-the-public-key"></a>Získání veřejného klíče  
 Zpoždění podepsání sestavení, musí mít přístup k veřejnému klíči. Můžete buď získat reálné veřejný klíč z organizace ve vaší společnosti, která provede konečnou podepisování, nebo vytvořit veřejný klíč pomocí [nástroj Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  
  
 Následující příkaz Sn.exe vytvoří pár test veřejného/soukromého klíče. **– K** možnost určuje, zda by měl vytvořit nový pár klíčů a uložte ho do souboru s názvem TestKeyPair.snk Sn.exe.  
  
```console
sn –k TestKeyPair.snk   
```  
  
 Extrahujte veřejný klíč ze souboru, který obsahuje pár klíčů testu. Následující příkaz extrahuje veřejný klíč z TestKeyPair.snk a uloží ho do PublicKey.snk:  
  
```console
sn –p TestKeyPair.snk PublicKey.snk  
```  
  
### <a name="delay-signing-an-assembly"></a>Zpoždění podepsání sestavení  
 Po Získejte nebo vytvořte veřejný klíč, můžete použít [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) pro kompilaci sestavení a určení zpožděného podepisování.  
  
 Následující příkaz Al.exe vytvoří silným názvem satelitní sestavení pro aplikaci StringLibrary ze souboru strings.ja.resources:  
  
```console 
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk  
```  
  
 **– Zpoždění +** možnost určuje, že propojovací program sestavení by měl zpoždění podepsání sestavení. **- Keyfile** Určuje název souboru s klíčem, který obsahuje veřejný klíč sloužící k odložení podepsání sestavení.  
  
### <a name="re-signing-an-assembly"></a>Znovu podepisování sestavení  
 Před nasazením aplikace ji musíte znovu podepsat zpoždění podepsané satelitní sestavení s reálné dvojice klíčů. Můžete to provést pomocí Sn.exe.  
  
 Následující příkaz Sn.exe podepíše StringLibrary.resources.dll párem klíčů uložených v souboru RealKeyPair.snk. **– R** možnost určuje, že dříve podepsaný nebo zpoždění je podepsané sestavení znovu podepsat.  
  
```console
sn –R StringLibrary.resources.dll RealKeyPair.snk   
```  
  
### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a>Instalace satelitní sestavení v globální mezipaměti sestavení  
 Když modul runtime hledá prostředky v procesu nalezení záložního prostředku, hledá v [globální mezipaměti sestavení](../../../docs/framework/app-domains/gac.md) první. (Další informace najdete v tématu v části "Proces záložního prostředku" [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) tématu.) Co nejdříve satelitní sestavení je podepsáno silným názvem, ho můžete nainstalovat v globální mezipaměti sestavení pomocí [Global Assembly Cache Tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
 Následující příkaz Gacutil.exe nainstaluje StringLibrary.resources.dll v globální mezipaměti sestavení:  
  
```console
gacutil -i:StringLibrary.resources.dll  
```  
  
 **/I** možnost určuje, že Gacutil.exe nainstalujte zadané sestavení do globální mezipaměti sestavení. Po satelitní sestavení je nainstalováno v mezipaměti, které obsahuje prostředky budou k dispozici pro všechny aplikace, které jsou určeny k použití satelitní sestavení.  
  
### <a name="resources-in-the-global-assembly-cache-an-example"></a>Prostředky v globální mezipaměti sestavení: Příklad  
 Následující příklad používá metodu v knihovně tříd rozhraní .NET Framework pro extrakci a vrátit lokalizované pozdrav ze souboru prostředků. Knihovny a její prostředky jsou registrovány v globální mezipaměti sestavení. Příklad obsahuje prostředky pro angličtinu (Spojené státy), francouzština (Francie), ruština (Rusko) a anglické jazykové verze. Je výchozí jazykovou verzi, angličtina její prostředky jsou uloženy v hlavním sestavení. V příkladu nejdřív zpoždění příznaky knihovny a jeho satelitních sestavení s veřejným klíčem, pak znovu podepíše je pomocí dvojice veřejného/soukromého klíče. Chcete-li vytvořit příklad, postupujte takto:  
  
1.  Pokud nepoužíváte Visual Studio, použijte následující [nástroj Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) příkaz pro vytvoření páru veřejného a privátního klíče s názvem ResKey.snk:  
  
    ```console
    sn –k ResKey.snk  
    ```  
  
     Pokud používáte Visual Studio, použijte **podepisování** kartu projektu **vlastnosti** dialogové okno pro vytvoření souboru klíče.  
  
2.  Pomocí následujících [nástroj Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) příkaz pro vytvoření souboru veřejného klíče s názvem PublicKey.snk:  
  
    ```console
    sn –p ResKey.snk PublicKey.snk  
    ```  
  
3.  Vytvoření souboru prostředků s názvem Strings.resx tak, aby obsahovala prostředků pro výchozí jazykovou verzi. Jeden řetězec s názvem Store `Greeting` jehož hodnota je "Jak proveďte vám?" v tomto souboru.  
  
4.  Označuje, že "en" výchozí jazykovou verzi aplikace, přidejte následující <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atribut souboru AssemblyInfo aplikace nebo souboru hlavní zdrojového kódu, který se zkompiluje do sestavení hlavní aplikace:  
  
     [!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
     [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]  
  
5.  Přidání podpory pro další jazykové verze (en US, fr-FR a ru-RU jazykové verze) aplikace následujícím způsobem:  
  
    -   Pro podporu "en US" nebo jazykové verze Angličtina (Spojené státy), vytvořit soubor prostředků s názvem Strings.en US.resx nebo Strings.en US.txt a do ní uložte jednoho řetězce s názvem `Greeting` jehož hodnota je "Hello!".  
  
    -   Pro podporu "fr-FR" nebo jazykovou verzi francouzština (Francie), vytvořit soubor prostředků s názvem Strings.fr-FR.resx nebo Strings.fr FR.txt a do ní uložte jednoho řetězce s názvem `Greeting` jehož hodnota je "Šťastnou jour!"  
  
    -   Pro podporu "ru-RU" nebo ruština (Rusko) jazykovou verzi, vytvořit soubor prostředků s názvem Strings.ru RU.resx nebo Strings.ru RU.txt a do ní uložte jednoho řetězce s názvem `Greeting` jehož hodnota je "Привет!"  
  
6.  Použití [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) kompilace jednotlivých textu nebo XML souboru prostředků do binárního souboru .resources. Výstupem je sada souborů, které mají stejný název kořenového souboru jako soubory RESX a txt, ale s příponou .resources. Pokud v příkladu vytvoříte pomocí sady Visual Studio, je automaticky zpracována proces kompilace. Pokud nepoužíváte Visual Studio, spusťte následující příkaz pro kompilaci souborů .resx na soubory .resources:  
  
    ```console
    resgen filename  
    ```  
  
     kde *filename* je volitelná cesta, název souboru a příponu souboru .resx nebo text.  
  
7.  Kompilace následující zdrojový kód z důvodu StringLibrary.vb nebo StringLibrary.cs spolu s prostředky pro výchozí jazykovou verzi na zpoždění podepsané sestavení knihovny s názvem StringLibrary.dll:  
  
    > [!IMPORTANT]
    >  Pokud používáte příkazového řádku namísto Visual Studio k vytvoření příkladu, byste měli upravit volání <xref:System.Resources.ResourceManager> konstruktor třídy, aby `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.  
  
     [!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
     [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]  
  
     Příkaz pro C# kompilátoru je:  
  
    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs  
    ```  
  
     Příkaz odpovídající kompilátoru jazyka Visual Basic je:  
  
    ```console  
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb  
    ```  
  
8.  Vytvořte podadresář v adresáři hlavní aplikace pro každou lokalizovanou jazykovou verzi podporováno v aplikaci. Měli byste vytvořit en US, fr-FR a podadresář ru-RU. Tyto podsložky Visual Studio automaticky vytvoří jako součást procesu kompilace. Vzhledem k tomu, že všechny satelitní sestavení se stejným názvem, podadresáře se používají k ukládání jednotlivé specifické pro jazykovou verzi satelitní sestavení, dokud jsou podepsány pomocí dvojice veřejného/soukromého klíče.  
  
9. Vkládání jednotlivých souborů .resources specifické pro jazykovou verzi do podepisováno satelitní sestavení a uloží je do příslušného adresáře. Příkaz pro každý soubor .resources je:  
  
    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk  
    ```  
  
     kde *jazykovou verzi* je název jazykové verze. V tomto příkladu jsou názvy jazykové verze en US, fr-FR a ru-RU.  
  
10. Znovu podepsat pomocí StringLibrary.dll [nástroj Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) následujícím způsobem:  
  
    ```console
    sn –R StringLibrary.dll RealKeyPair.snk  
    ```  
  
11. Znovu podepište jednotlivé satelitních sestavení. Chcete-li to provést, použijte [nástroj Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) následujícím způsobem pro každou satelitní sestavení:  
  
    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk  
    ```  
  
12. Zaregistrujte StringLibrary.dll a každá z jeho satelitních sestavení v globální mezipaměti sestavení pomocí následujícího příkazu:  
  
    ```console
    gacutil -i filename  
    ```  
  
     kde *filename* je název souboru k registraci.  
  
13. Pokud používáte Visual Studio, vytvořte nový **konzolovou aplikaci** projekt s názvem `Example`, přidejte do ní odkaz na StringLibrary.dll a následující zdrojový kód a zkompilovat.  
  
     [!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
     [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]  
  
     Pro kompilaci z příkazového řádku, použijte následující příkaz pro C# kompilátoru:  
  
    ```console
    csc Example.cs -r:StringLibrary.dll   
    ```  
  
     Příkazového řádku pro kompilátor jazyka Visual Basic je:  
  
    ```console
    vbc Example.vb -r:StringLibrary.dll   
    ```  
  
14. Spusťte Example.exe.  
  
## <a name="see-also"></a>Viz také:

- [Zabalení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Zpoždění podepsání sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (nástroj pro silný název)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Gacutil.exe (nástroj globální mezipaměti sestavení)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
- [Prostředky v aplikacích klasické pracovní plochy](../../../docs/framework/resources/index.md)
