---
title: Tlbimp.exe (importér knihovny typů)
ms.date: 03/30/2017
helpviewer_keywords:
- type libraries [.NET Framework], importing
- importing type library
- Tlbimp.exe
- type definition conversion
- Type Library Importer
- type libraries
- converting type definitions
ms.assetid: ec0a8d63-11b3-4acd-b398-da1e37e97382
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d28c5e817e415e08c3a58c840e52cdfcbe286997
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409825"
---
# <a name="tlbimpexe-type-library-importer"></a>Tlbimp.exe (importér knihovny typů)
Nástroj Type Library Importer převádí definice typu nalezené v knihovně typů modelu COM na ekvivalentní definice v sestavení Common Language Runtime. Výstupem nástroje Tlbimp.exe je binární soubor (sestavení) obsahující metadata modulu runtime pro typy definované v rámci původní knihovny typů. Můžete zkontrolovat tento soubor s nástroji, jako [Ildasm.exe](ildasm-exe-il-disassembler.md).  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
tlbimp tlbFile [options]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*tlbFile*|Název jakéhokoli souboru obsahujícího knihovnu typů modelu COM.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/asmversion:** *číslo verze*|Určuje číslo verze vytvářeného sestavení. Zadejte *cisloverze* ve formátu *major.minor.build.revision*.|  
|**/ Společnost:** `companyinformation`|Přidá informace o společnosti do výstupního sestavení.|  
|**OutDir delaysign/Copyright:** `copyrightinformation`|Přidá informace o autorských právech do výstupního sestavení. Tyto informace lze zobrazit v **vlastnosti souboru** dialogové okno pro sestavení.|  
|**/delaysign**|Říká nástroji Tlbimp.exe, aby podepsal výsledné sestavení se silným názvem pomocí zpožděného podepisování. Tato možnost je nutné zadat s buď **/keycontainer:**, **/keyfile:**, nebo **/publickey:** možnost. Další informace o procesu zpožděné podepisování najdete v tématu [zpoždění podepsání sestavení](../app-domains/delay-sign-assembly.md).|  
|**/ Help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/ keycontainer:** *containername*|Podepíše výsledné sestavení se silným názvem pomocí pár veřejného a privátního klíče najít v kontejneru klíčů určeného *containername*.|  
|**/ keyfile:** *filename*|Podepíše výsledné sestavení se silným názvem pomocí vydavatele oficiální pár veřejného a privátního klíče v nalezen *filename*.|  
|**/machine:** `machinetype`|Vytvoří sestavení určené pro konkrétní typ počítače (mikroprocesoru). Podporované typy počítačů: x86, x64, Itanium a Agnostic.|  
|**/ NAMESPACE:** *obor názvů*|Určuje obor názvů, ve kterém se má vytvořit sestavení.|  
|**/noclassmembers**|Zabraňuje nástroji Tlbimp.exe v přidávání členů do tříd. Tím je zabráněno potenciální <xref:System.TypeLoadException>.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/ out:** *filename*|Určuje název výstupního souboru, sestavení a oboru názvů, do kterých chcete zapsat definice metadat. **/Out** možnost nemá žádný vliv na obor názvů je sestavení, pokud knihovny typů určuje vlastní atribut definice jazyka IDL (Interface), který explicitně ovládací prvky oboru názvů je sestavení. Pokud tuto možnost nezadáte, nástroj Tlbimp.exe zapíše metadata do souboru se stejným názvem, jaký má skutečná knihovna typů definovaná v rámci vstupního souboru, a přiřadí mu příponu .dll. Pokud má výstupní soubor stejný název jako vstupní soubor, nástroj vygeneruje chybu bránící přepsání knihovny typů.|  
|**/ primární**|Vytvoří primární sestavení zprostředkovatele komunikace pro zadanou knihovnu typů. Do sestavení jsou vloženy informace o tom, že toto sestavení vytvořil vydavatel knihovny typů. Zadáním primárního sestavení zprostředkovatele komunikace odlišíte sestavení vydavatele od ostatních sestavení vytvořených z knihovny typů používající nástroj Tlbimp.exe. Byste měli používat jenom **/primární** možnost, pokud jste vydavatele knihovny typů, který chcete importovat pomocí Tlbimp.exe. Všimněte si, že, musíte se odhlásit primární spolupracující sestavení s [silným názvem](../app-domains/strong-named-assemblies.md). Další informace najdete v tématu [primární zprostředkovatel komunikace s objekty sestavení](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).|  
|**/Product:** `productinformation`|Přidá informace o produktu do výstupního sestavení. Tyto informace lze zobrazit v **vlastnosti souboru** dialogové okno pro sestavení.|  
|**/ProductVersion:** `productversioninformation`|Přidá informace o verzi produktu do výstupního sestavení. Neexistují žádná omezení formátu. Tyto informace lze zobrazit v **vlastnosti souboru** dialogové okno pro sestavení.|  
|**/publicKey:** *filename*|Určuje soubor obsahující veřejný klíč pro použití k podepsání výsledného sestavení. Pokud zadáte **/keyfile:** nebo **/keycontainer:** možnost místo **/publickey:**, Tlbimp.exe generuje veřejný klíč z pár veřejného a privátního klíče, součástí **/keyfile:** nebo **/keycontainer:**. **/Publickey:** podporuje možnost otestovat klíč a zpoždění podepsání scénáře. Soubor má formát generovaný nástrojem Sn.exe. Další informace najdete v tématu **-p** možnost Sn.exe v [Strong Name Tool (Sn.exe)](sn-exe-strong-name-tool.md).|  
|**/ reference:** *filename*|Určuje soubor sestavení, který se má použít při řešení odkazů na typy definované mimo aktuální knihovnu typů. Pokud nezadáte **/reference** možnost, Tlbimp.exe automaticky rekurzivně importuje všechny externí typ knihovny, typu knihovny importovaných odkazy. Pokud zadáte **/reference** možnost, nástroj pokusí přeložit externí typy v odkazovaných sestaveních, než ho importuje jiné knihovny typů.|  
|**/silence:** `warningnumber`|Potlačí zobrazení konkrétního upozornění. Tuto možnost nelze použít s **/tichou**.|  
|**/ tichou**|Potlačí zobrazování zpráv o úspěšném dokončení. Tuto možnost nelze použít s **/ticho**.|  
|**/strictref**|Neimportuje knihovny typů, pokud nástroj nemůže vyřešit všechny odkazy v rámci aktuální sestavení, sestavení, zadaný **/reference** možnost nebo registrovaný primární spolupracující sestavení (PIA).|  
|**/strictref:nopia**|Stejné jako **/strictref**, ale ignoruje PIA.|  
|**/sysarray**|Určuje, že nástroj pro import COM styl SafeArray jako spravované <xref:System.Array> typu.|  
|**/tlbreference:** *filename*|Určuje soubor knihovny typů, který se má použít k vyřešení odkazů knihovny typů bez konzultace s registrem.<br /><br /> Tato možnost nenačte některé starší formáty knihovny typů.  Stále však můžete načíst starší formáty knihovny typů implicitně pomocí registru nebo aktuálního adresáře.|  
|**/Trademark:** `trademarkinformation`|Přidá informace o obchodní známce do výstupního sestavení. Tyto informace lze zobrazit v **vlastnosti souboru** dialogové okno pro sestavení.|  
|**/ transformace:** *transformname*|Transformuje metadata podle specifikace *transformname* parametr.<br /><br /> Zadejte **dispret** pro *transformname* parametr transformace [na více systémů, retval] Parametry metod na určené pouze pro rozhraní (odesílající rozhraní) do návratové hodnoty.<br /><br /> Další informace o této možnosti naleznete v příkladech dále v tomto tématu.|  
|**/ unsafe**|Vytvoří rozhraní bez kontroly zabezpečení rozhraní .NET Framework. Volání metody, která je vystavena tímto způsobem, může představovat bezpečnostní riziko. Tuto možnost nepoužívejte, pokud si nejste vědomi rizika vystavení takového kódu.|  
|**/verbose**|Určuje režim podrobného vypisování; zobrazí další informace o importované knihovně typů.|  
|**/VariantBoolFieldToBool**|Převede `VARIANT_BOOL` polí v struktur <xref:System.Boolean>.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
> [!NOTE]
>  Možnosti příkazového řádku pro nástroj Tlbimp.exe nerozlišují malá a velká písmena a lze je zadat v libovolném pořadí. Pro jednoznačnou identifikaci je potřeba pouze poskytnout dostatek parametrů. Proto **/n** je ekvivalentní **/nologo** a **/OU:** *outfile.dll* je ekvivalentní **/out:**  *OutFile.dll*.  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Tlbimp.exe provádí převody celé knihovny typů najednou. Pomocí tohoto nástroje nelze generovat informace pro podmnožinu typů definovaných v rámci jedné knihovny typů.  
  
 Je často užitečné nebo které jsou nezbytné, abyste mohli přiřadit [silné názvy](../app-domains/strong-named-assemblies.md) na sestavení. Proto nástroj Tlbimp.exe obsahuje možnosti pro poskytnutí informací nezbytných k vytvoření sestavení se silným názvem. Obě **/keyfile:** a **/keycontainer:** možnosti podepsání sestavení se silnými názvy. Je tedy logické zadat vždy pouze jednu z těchto možností.  
  
 Můžete zadat několik referenční sestavení pomocí **/reference** možnost vícekrát.  
  
 ID prostředku lze volitelně připojit k souboru knihovny typů při importu knihovny typů z modulu obsahujícího více knihoven typů. Nástroj Tlbimp.exe je schopen najít tento soubor pouze v případě, že se nachází v aktuálním adresáři, nebo pokud zadáte úplnou cestu. Podívejte se na příklad dále v tomto tématu.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz generuje sestavení se stejným názvem jako knihovny typů v `myTest.tlb` a s příponou .dll.  
  
```  
tlbimp myTest.tlb   
```  
  
 Následující příkaz generuje sestavení s názvem `myTest.dll`.  
  
```  
tlbimp  myTest.tlb  /out:myTest.dll  
```  
  
 Následující příkaz generuje sestavení se stejným názvem jako knihovnu typů určenou ve `MyModule.dll\1` a s příponou .dll. `MyModule.dll\1` musí být umístěny v aktuálním adresáři.  
  
```  
tlbimp MyModule.dll\1  
```  
  
 Následující příkaz generuje sestavení s názvem `myTestLib.dll` knihovny typů `TestLib.dll`. **/Transform:dispret** možnost transformuje žádné [mimo, retval] Parametry metody pro odesílající rozhraní v knihovně typu do návratové hodnoty ve spravované knihovně.  
  
```  
tlbimp TestLib.dll /transform:dispret /out:myTestLib.dll  
```  
  
 Knihovny typů `TestLib.dll`, v předchozím příkladu obsahuje dispinterface metodu s názvem `SomeMethod` , vrátí prázdnou hodnotu a má [mimo, retval] parametr. Následující kód je podpis metody knihovny typ vstupu pro `SomeMethod` v `TestLib.dll`.  
  
```  
void SomeMethod([out, retval] VARIANT_BOOL*);  
```  
  
 Určení **/transform:dispret** Tlbimp.exe k transformaci způsobí, že `[out, retval]` parametr `SomeMethod` do `bool` vrátit hodnotu. Toto je metoda podpisu, který vytváří Tlbimp.exe pro `SomeMethod` ve spravované knihovně `myTestLib.dll` při **/transform:dispret** je zadána možnost.  
  
```csharp  
bool SomeMethod();  
```  
  
 Pokud použijete k vytvoření spravovanou knihovnu pro Tlbimp.exe `TestLib.dll` bez zadání **/transform:dispret**, nástroj vytvoří následující podpis metody pro `SomeMethod` ve spravované knihovně `myTestLib.dll`.  
  
```csharp  
void SomeMethod(out bool x);  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](index.md)  
 [Tlbexp.exe (exportér knihovny typů)](tlbexp-exe-type-library-exporter.md)  
 [Import knihovny typů ve formě sestavení](../interop/importing-a-type-library-as-an-assembly.md)  
 [Knihovny typů pro souhrn konverze sestavení](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100))  
 [Ildasm.exe (IL Disassembler)](ildasm-exe-il-disassembler.md)  
 [Sn.exe (nástroj pro silný název)](sn-exe-strong-name-tool.md)  
 [Sestavení se silným názvem](../app-domains/strong-named-assemblies.md)  
 [Atributy pro import knihovny typů do spolupráce – sestavení](https://msdn.microsoft.com/library/81e587b8-393f-43e1-9add-c4b05e65cbfd(v=vs.100))  
 [Příkazové řádky](developer-command-prompt-for-vs.md)
