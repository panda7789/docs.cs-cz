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
ms.openlocfilehash: da36cfb86aae52af90451e92b8b17088e29481da
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481752"
---
# <a name="tlbimpexe-type-library-importer"></a>Tlbimp.exe (importér knihovny typů)
Nástroj Type Library Importer převádí definice typu nalezené v knihovně typů modelu COM na ekvivalentní definice v sestavení Common Language Runtime. Výstupem nástroje Tlbimp.exe je binární soubor (sestavení) obsahující metadata modulu runtime pro typy definované v rámci původní knihovny typů. Tento soubor s nástroji můžete zkontrolovat, jako [Ildasm.exe](ildasm-exe-il-disassembler.md).  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
tlbimp tlbFile [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*tlbFile*|Název jakéhokoli souboru obsahujícího knihovnu typů modelu COM.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/asmversion:** *číslo_verze*|Určuje číslo verze vytvářeného sestavení. Zadejte *číslo_verze* ve formátu *major.minor.build.revision*.|  
|**/ Company:** `companyinformation`|Přidá informace o společnosti do výstupního sestavení.|  
|**/Copyright:** `copyrightinformation`|Přidá informace o autorských právech do výstupního sestavení. Tyto informace můžete zobrazit v **vlastnosti souboru** dialogové okno pro sestavení.|  
|**/delaysign**|Říká nástroji Tlbimp.exe, aby podepsal výsledné sestavení se silným názvem pomocí zpožděného podepisování. Tuto možnost musíte zadat buď **/keycontainer:**, **/keyfile:**, nebo **/publickey:** možnost. Další informace o procesu zpožděného podepisování naleznete v tématu [zpožděné podepisování sestavení](../app-domains/delay-sign-assembly.md).|  
|**/ Help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/ keycontainer:** *containername*|Podepisuje výsledné sestavení se silným názvem pomocí dvojice veřejného/soukromého klíče nacházející v kontejneru klíčů určeném parametrem *containername*.|  
|**/ keyfile:** *název souboru*|Podepisuje výsledné sestavení se silným názvem pomocí vydavatele dvojice oficiálního veřejného/soukromého klíče v *filename*.|  
|**/ machine:** `machinetype`|Vytvoří sestavení určené pro konkrétní typ počítače (mikroprocesoru). Podporované typy počítačů: x86, x64, Itanium a Agnostic.|  
|**/ NAMESPACE:** *obor názvů*|Určuje obor názvů, ve kterém se má vytvořit sestavení.|  
|**/noclassmembers**|Zabraňuje nástroji Tlbimp.exe v přidávání členů do tříd. Tím se vyhnete případné <xref:System.TypeLoadException>.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/ out:** *název souboru*|Určuje název výstupního souboru, sestavení a oboru názvů, do kterých chcete zapsat definice metadat. **/Out** možnost nemá žádný vliv na obor názvů sestavení, pokud typ knihovny určuje vlastní atribut Interface Definition Language (IDL), který explicitně kontroluje obor názvů sestavení. Pokud tuto možnost nezadáte, nástroj Tlbimp.exe zapíše metadata do souboru se stejným názvem, jaký má skutečná knihovna typů definovaná v rámci vstupního souboru, a přiřadí mu příponu .dll. Pokud má výstupní soubor stejný název jako vstupní soubor, nástroj vygeneruje chybu bránící přepsání knihovny typů.|  
|**/ primární**|Vytvoří primární sestavení zprostředkovatele komunikace pro zadanou knihovnu typů. Do sestavení jsou vloženy informace o tom, že toto sestavení vytvořil vydavatel knihovny typů. Zadáním primárního sestavení zprostředkovatele komunikace odlišíte sestavení vydavatele od ostatních sestavení vytvořených z knihovny typů používající nástroj Tlbimp.exe. Byste měli používat jenom **/primary** možnost, pokud jste vydavatel knihovny typů, kterou importujete pomocí Tlbimp.exe. Všimněte si, že primární sestavení zprostředkovatele komunikace s musíte podepsat [silným názvem](../app-domains/strong-named-assemblies.md). Další informace najdete v tématu [Primary Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).|  
|**/Product:** `productinformation`|Přidá informace o produktu do výstupního sestavení. Tyto informace můžete zobrazit v **vlastnosti souboru** dialogové okno pro sestavení.|  
|**/ProductVersion:** `productversioninformation`|Přidá informace o verzi produktu do výstupního sestavení. Neexistují žádná omezení formátu. Tyto informace můžete zobrazit v **vlastnosti souboru** dialogové okno pro sestavení.|  
|**/publicKey:** *název souboru*|Určuje soubor obsahující veřejný klíč pro použití k podepsání výsledného sestavení. Pokud zadáte **/keyfile:** nebo **/keycontainer:** možnost místo **/publickey:**, Tlbimp.exe vygeneruje veřejný klíč z dvojice veřejného/soukromého klíče, součástí **/keyfile:** nebo **/keycontainer:**. **/Publickey:** možnost podporuje testovací klíč a scénáře se zpožděným podepisováním. Soubor má formát generovaný nástrojem Sn.exe. Další informace najdete v tématu **-p** – možnost nástroje Sn.exe v [nástroj Strong Name (Sn.exe)](sn-exe-strong-name-tool.md).|  
|**/ reference:** *název souboru*|Určuje soubor sestavení, který se má použít při řešení odkazů na typy definované mimo aktuální knihovnu typů. Pokud nezadáte **/reference** možnost, Tlbimp.exe automaticky rekurzivně importuje všechny externí knihovny typů, se importovaná knihovna typů odkazů. Pokud zadáte **/reference** možnost, nástroj se pokusí přeložit externí typy v odkazovaných sestaveních, než importuje další knihovny typů.|  
|**/silence:** `warningnumber`|Potlačí zobrazení konkrétního upozornění. Tento parametr nelze použít s **/silent**.|  
|**/ silent**|Potlačí zobrazování zpráv o úspěšném dokončení. Tento parametr nelze použít s **/nečinnosti**.|  
|**/strictref**|Neprovede import knihovny typů Pokud nástroj nemůže vyřešit všechny odkazy v rámci aktuálního sestavení, sestavení zadaných pomocí **/reference** možnost nebo registrovaných primárních spolupracujících sestavení (PIA).|  
|**/strictref:nopia**|Stejné jako **/strictref**, ale ignoruje PIA.|  
|**/sysarray**|Určuje, že nástroj má importovat styl SafeArray modelu COM jako spravovaný <xref:System.Array> typu.|  
|**/tlbreference:** *název souboru*|Určuje soubor knihovny typů, který se má použít k vyřešení odkazů knihovny typů bez konzultace s registrem.<br /><br /> Tato možnost nenačte některé starší formáty knihovny typů.  Stále však můžete načíst starší formáty knihovny typů implicitně pomocí registru nebo aktuálního adresáře.|  
|**/Trademark:** `trademarkinformation`|Přidá informace o obchodní známce do výstupního sestavení. Tyto informace můžete zobrazit v **vlastnosti souboru** dialogové okno pro sestavení.|  
|**/transform:** *transformname*|Transformuje metadata podle *transformname* parametru.<br /><br /> Zadejte **dispret** pro *transformname* parametrů na parametry transformace [out, retval] metod v určené pouze pro rozhraní (odesílající rozhraní) na návratové hodnoty.<br /><br /> Další informace o této možnosti naleznete v příkladech dále v tomto tématu.|  
|**/unsafe**|Vytvoří rozhraní bez kontroly zabezpečení rozhraní .NET Framework. Volání metody, která je vystavena tímto způsobem, může představovat bezpečnostní riziko. Tuto možnost nepoužívejte, pokud si nejste vědomi rizika vystavení takového kódu.|  
|**/verbose**|Určuje režim podrobného vypisování; zobrazí další informace o importované knihovně typů.|  
|**/VariantBoolFieldToBool**|Převede `VARIANT_BOOL` pole ve strukturách na <xref:System.Boolean>.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
> [!NOTE]
>  Možnosti příkazového řádku pro nástroj Tlbimp.exe nerozlišují malá a velká písmena a lze je zadat v libovolném pořadí. Pro jednoznačnou identifikaci je potřeba pouze poskytnout dostatek parametrů. Proto **/n** je ekvivalentní **/nologo** a **/OU:** *outfile.dll* je ekvivalentní **/out:**  *OutFile.dll*.  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Tlbimp.exe provádí převody celé knihovny typů najednou. Pomocí tohoto nástroje nelze generovat informace pro podmnožinu typů definovaných v rámci jedné knihovny typů.  
  
 Často je užitečné nebo nutné moci přiřadit [silných názvů](../app-domains/strong-named-assemblies.md) na sestavení. Proto nástroj Tlbimp.exe obsahuje možnosti pro poskytnutí informací nezbytných k vytvoření sestavení se silným názvem. Oba **/keyfile:** a **/keycontainer:** možnosti podepsat sestavení se silnými názvy. Je tedy logické zadat vždy pouze jednu z těchto možností.  
  
 Můžete zadat více odkazů na sestavení s použitím **/reference** možnost více než jednou.  
  
 ID prostředku lze volitelně připojit k souboru knihovny typů při importu knihovny typů z modulu obsahujícího více knihoven typů. Nástroj Tlbimp.exe je schopen najít tento soubor pouze v případě, že se nachází v aktuálním adresáři, nebo pokud zadáte úplnou cestu. Podívejte se na příklad dále v tomto tématu.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz vygeneruje sestavení se stejným názvem jako knihovny typů nacházející se v `myTest.tlb` a s příponou .dll.  
  
```  
tlbimp myTest.tlb   
```  
  
 Následující příkaz vygeneruje sestavení s názvem `myTest.dll`.  
  
```  
tlbimp  myTest.tlb  /out:myTest.dll  
```  
  
 Následující příkaz vygeneruje sestavení se stejným názvem jako knihovny typů určené souborem `MyModule.dll\1` a s příponou .dll. `MyModule.dll\1` musí být umístěny v aktuálním adresáři.  
  
```  
tlbimp MyModule.dll\1  
```  
  
 Následující příkaz vygeneruje sestavení s názvem `myTestLib.dll` pro knihovnu typů `TestLib.dll`. **/Transform:dispret** možnost transformuje všechny [out, retval] metod v odesílacích rozhraních v knihovně typů na návratové hodnoty ve spravované knihovně parametry.  
  
```  
tlbimp TestLib.dll /transform:dispret /out:myTestLib.dll  
```  
  
 Knihovna typů `TestLib.dll`, v předchozím příkladu obsahuje metodu odesílajícího rozhraní nazvanou `SomeMethod` , který vrací hodnotu void a má [out, retval] parametru. Následující kód představuje podpis vstupní typ knihovny metody pro `SomeMethod` v `TestLib.dll`.  
  
```  
void SomeMethod([out, retval] VARIANT_BOOL*);  
```  
  
 Zadání **/transform:dispret** možnost způsobí, že Tlbimp.exe k transformaci `[out, retval]` parametr `SomeMethod` do `bool` návratovou hodnotu. Následuje podpis metody, která Tlbimp.exe vytváří pro `SomeMethod` ve spravované knihovně `myTestLib.dll` při **/transform:dispret** je zadána možnost.  
  
```csharp  
bool SomeMethod();  
```  
  
 Pokud používáte Tlbimp.exe k vytvoření spravované knihovny pro `TestLib.dll` bez zadání **/transform:dispret**, nástroj vytvoří následující podpis metody pro `SomeMethod` ve spravované knihovně `myTestLib.dll`.  
  
```csharp  
void SomeMethod(out bool x);  
```  
  
## <a name="see-also"></a>Viz také:
- [Nástroje](index.md)
- [Tlbexp.exe (exportér knihovny typů)](tlbexp-exe-type-library-exporter.md)
- [Import knihovny typů ve formě sestavení](../interop/importing-a-type-library-as-an-assembly.md)
- [Souhrn převodu sestavení knihovny typů na](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Ildasm.exe (IL Disassembler)](ildasm-exe-il-disassembler.md)
- [Sn.exe (nástroj pro silný název)](sn-exe-strong-name-tool.md)
- [Sestavení se silným názvem](../app-domains/strong-named-assemblies.md)
- [Atributy pro import knihoven typů do sestavení vzájemné spolupráce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y6a7ak23(v=vs.100))
- [Příkazové řádky](developer-command-prompt-for-vs.md)
