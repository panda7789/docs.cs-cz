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
ms.openlocfilehash: d942378888b06049022188c75456f438d4b187e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180248"
---
# <a name="tlbimpexe-type-library-importer"></a>Tlbimp.exe (importér knihovny typů)
Nástroj Type Library Importer převádí definice typu nalezené v knihovně typů modelu COM na ekvivalentní definice v sestavení Common Language Runtime. Výstupem nástroje Tlbimp.exe je binární soubor (sestavení) obsahující metadata modulu runtime pro typy definované v rámci původní knihovny typů. Tento soubor můžete prozkoumat pomocí nástrojů, jako je [ildasm.exe](ildasm-exe-il-disassembler.md).  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
tlbimp tlbFile [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*soubor tlb*|Název jakéhokoli souboru obsahujícího knihovnu typů modelu COM.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/asmversion:** *číslo verze*|Určuje číslo verze vytvářeného sestavení. Zadejte *číslo verze* ve formátu *major.minor.build.revision*.|  
|**/společnost:**`companyinformation`|Přidá informace o společnosti do výstupního sestavení.|  
|**/autorská práva:**`copyrightinformation`|Přidá informace o autorských právech do výstupního sestavení. Tyto informace lze zobrazit v dialogovém okně **Vlastnosti souboru** pro sestavení.|  
|**/delaysign**|Říká nástroji Tlbimp.exe, aby podepsal výsledné sestavení se silným názvem pomocí zpožděného podepisování. Tuto možnost je nutné zadat buď s parametrem **/keycontainer:**, **/keyfile:** nebo **/publickey:** option. Další informace o procesu zpožděného podepisování naleznete v [tématu Delay Signing a Assembly](../../standard/assembly/delay-sign.md).|  
|**/nápověda**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/keycontainer:** *název kontejneru*|Podepisuje výsledné sestavení silným názvem pomocí dvojice veřejného a soukromého klíče nalezené v kontejneru klíčů určeném *názvem kontejneru*.|  
|**/keyfile:** *název souboru*|Výsledné sestavení podeveje silným názvem pomocí oficiálnídvojice veřejného a soukromého klíče vydavatele, která se nachází v *názvu souboru*.|  
|**/stroj:**`machinetype`|Vytvoří sestavení určené pro konkrétní typ počítače (mikroprocesoru). Podporované typy počítačů: x86, x64, Itanium a Agnostic.|  
|**/obor názvů:** *obor názvů*|Určuje obor názvů, ve kterém se má vytvořit sestavení.|  
|**/noclassmembers**|Zabraňuje nástroji Tlbimp.exe v přidávání členů do tříd. Tím se zabrání <xref:System.TypeLoadException>potenciálu .|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/out:** *název souboru*|Určuje název výstupního souboru, sestavení a oboru názvů, do kterých chcete zapsat definice metadat. Možnost **/out** nemá žádný vliv na obor názvů sestavení, pokud knihovna typů určuje vlastní atribut IDL (Interface Definition Language), který explicitně řídí obor názvů sestavení. Pokud tuto možnost nezadáte, nástroj Tlbimp.exe zapíše metadata do souboru se stejným názvem, jaký má skutečná knihovna typů definovaná v rámci vstupního souboru, a přiřadí mu příponu .dll. Pokud má výstupní soubor stejný název jako vstupní soubor, nástroj vygeneruje chybu bránící přepsání knihovny typů.|  
|**/primární**|Vytvoří primární sestavení zprostředkovatele komunikace pro zadanou knihovnu typů. Do sestavení jsou vloženy informace o tom, že toto sestavení vytvořil vydavatel knihovny typů. Zadáním primárního sestavení zprostředkovatele komunikace odlišíte sestavení vydavatele od ostatních sestavení vytvořených z knihovny typů používající nástroj Tlbimp.exe. /primary možnost **/primary** byste měli použít pouze v případě, že jste vydavatelem knihovny typů, kterou importujete pomocí souboru Tlbimp.exe. Všimněte si, že musíte podepsat primární sestavení interop se [silným názvem](../../standard/assembly/strong-named.md). Další informace naleznete v [tématu Primární interop sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).|  
|**/produkt:**`productinformation`|Přidá informace o produktu do výstupního sestavení. Tyto informace lze zobrazit v dialogovém okně **Vlastnosti souboru** pro sestavení.|  
|**/productversion:**`productversioninformation`|Přidá informace o verzi produktu do výstupního sestavení. Neexistují žádná omezení formátu. Tyto informace lze zobrazit v dialogovém okně **Vlastnosti souboru** pro sestavení.|  
|**/publickey:** *název souboru*|Určuje soubor obsahující veřejný klíč pro použití k podepsání výsledného sestavení. Pokud zadáte **parametr /keyfile:** nebo **/keycontainer:** možnost namísto **/publickey:**, program Tlbimp.exe vygeneruje veřejný klíč z dvojice veřejného a soukromého klíče dodávané se **souborem /keyfile:** nebo **/keycontainer:**. **Možnost /publickey:** podporuje testovací klíč a zpoždění scénářů podepisování. Soubor má formát generovaný nástrojem Sn.exe. Další informace naleznete v možnosti **-p** sn.exe v [nástroji Silný název (Sn.exe)](sn-exe-strong-name-tool.md).|  
|**/reference:** *název souboru*|Určuje soubor sestavení, který se má použít při řešení odkazů na typy definované mimo aktuální knihovnu typů. Pokud nezadáte **/reference** možnost, Tlbimp.exe automaticky rekurzivně importuje všechny externí knihovny typů, které knihovna typů, které jsou importovány odkazy. Pokud zadáte **/reference** možnost, nástroj se pokusí vyřešit externí typy v odkazovaných sestaveních před importem jiných knihoven typů.|  
|**/ticho:**`warningnumber`|Potlačí zobrazení konkrétního upozornění. Tuto možnost nelze použít s **parametrem /silent**.|  
|**/silent**|Potlačí zobrazování zpráv o úspěšném dokončení. Tuto možnost nelze použít s **parametrem /silence**.|  
|**/strictref**|Neimportuje knihovnu typů, pokud nástroj nemůže vyřešit všechny odkazy v rámci aktuálního sestavení, sestavení určená volbou **/reference** nebo registrovaná primární meziop sestavení (PIA).|  
|**/strictref:nopia**|Stejné jako **/strictref**, ale ignoruje PIA.|  
|**/sysarray**|Určuje, že nástroj importuje styl COM <xref:System.Array> SafeArray jako spravovaný typ.|  
|**/tlbreference:** *název souboru*|Určuje soubor knihovny typů, který se má použít k vyřešení odkazů knihovny typů bez konzultace s registrem.<br /><br /> Tato možnost nenačte některé starší formáty knihovny typů.  Stále však můžete načíst starší formáty knihovny typů implicitně pomocí registru nebo aktuálního adresáře.|  
|**/ochranná známka:**`trademarkinformation`|Přidá informace o obchodní známce do výstupního sestavení. Tyto informace lze zobrazit v dialogovém okně **Vlastnosti souboru** pro sestavení.|  
|**/transform:** *název_transformace*|Transformuje metadata určená parametrem *transformname.*<br /><br /> Zadejte **dispret** pro parametr *transformace* [out, retval] metod na rozhraních pouze pro odeslání (dispinterfaces) do vrácených hodnot.<br /><br /> Další informace o této možnosti naleznete v příkladech dále v tomto tématu.|  
|**/nebezpečné**|Vytvoří rozhraní bez kontroly zabezpečení rozhraní .NET Framework. Volání metody, která je vystavena tímto způsobem, může představovat bezpečnostní riziko. Tuto možnost nepoužívejte, pokud si nejste vědomi rizika vystavení takového kódu.|  
|**/podrobné informace**|Určuje režim podrobného vypisování; zobrazí další informace o importované knihovně typů.|  
|**/VariantBoolFieldToBool**|Převede `VARIANT_BOOL` pole ve <xref:System.Boolean>strukturách na .|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
> [!NOTE]
> Možnosti příkazového řádku pro nástroj Tlbimp.exe nerozlišují malá a velká písmena a lze je zadat v libovolném pořadí. Pro jednoznačnou identifikaci je potřeba pouze poskytnout dostatek parametrů. Proto **/n** je ekvivalentní **/nologo** a **/ou:** *outfile.dll* je ekvivalentní **/out:** *outfile.dll*.  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Tlbimp.exe provádí převody celé knihovny typů najednou. Pomocí tohoto nástroje nelze generovat informace pro podmnožinu typů definovaných v rámci jedné knihovny typů.  
  
 Je často užitečné nebo nezbytné, aby bylo možné přiřadit [silné názvy](../../standard/assembly/strong-named.md) sestavení. Proto nástroj Tlbimp.exe obsahuje možnosti pro poskytnutí informací nezbytných k vytvoření sestavení se silným názvem. Oba **/keyfile:** a **/keycontainer:** možnosti podepsat sestavení se silnými názvy. Je tedy logické zadat vždy pouze jednu z těchto možností.  
  
 Více referenčních sestavení můžete zadat pomocí možnosti **/reference** vícekrát.

 Vzhledem ke způsobu, jakým tlbimp.exe generuje sestavení, není možné znovu zacílit sestavení na jinou `mscorlib` verzi. Například pokud chcete generovat sestavení, které se zaměřuje na rozhraní .NET Framework 2.0, tlbimp.exe dodávány s .NET Framework 2.0/3.0/3.5 SDK musí být použit. Chcete-li cílit na rozhraní .NET Framework 4.x, měl by být použit soubor Tlbimp.exe dodávaný s sadou .NET Framework 4.x SDK.

 ID prostředku lze volitelně připojit k souboru knihovny typů při importu knihovny typů z modulu obsahujícího více knihoven typů. Nástroj Tlbimp.exe je schopen najít tento soubor pouze v případě, že se nachází v aktuálním adresáři, nebo pokud zadáte úplnou cestu. Podívejte se na příklad dále v tomto tématu.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz generuje sestavení se stejným názvem jako knihovna typů nalezená v `myTest.tlb` příponě DLL a s příponou DLL.  
  
```console  
tlbimp myTest.tlb
```  
  
 Následující příkaz generuje sestavení s `myTest.dll`názvem .  
  
```console  
tlbimp  myTest.tlb  /out:myTest.dll  
```  
  
 Následující příkaz generuje sestavení se stejným názvem jako knihovna typů zadaná `MyModule.dll\1` příponou DLL a s ní. `MyModule.dll\1`musí být umístěn v aktuálním adresáři.  
  
```console  
tlbimp MyModule.dll\1  
```  
  
 Následující příkaz generuje sestavení s `myTestLib.dll` názvem knihovny `TestLib.dll`typů . Možnost **/transform:dispret** transformuje všechny parametry [out, retval] metod na dispinterfaces v knihovně typů na vrácené hodnoty ve spravované knihovně.  
  
```console  
tlbimp TestLib.dll /transform:dispret /out:myTestLib.dll  
```  
  
 Knihovna `TestLib.dll`typů v předchozím příkladu obsahuje metodu dispinterface s názvem, `SomeMethod` která vrací parametr void a má parametr [out, retval]. Následující kód je podpis metody knihovny vstupního typu pro `SomeMethod` v `TestLib.dll`.  
  
```cpp  
void SomeMethod([out, retval] VARIANT_BOOL*);  
```  
  
 Zadání možnosti **/transform:dispret** způsobí, že nástroj Tlbimp.exe transformuje `[out, retval]` `SomeMethod` parametr na vrácenou `bool` hodnotu. Následuje podpis metody, který tlbimp.exe `SomeMethod` vytváří pro `myTestLib.dll` ve spravované knihovně, když je zadána možnost **/transform:dispret.**  
  
```csharp  
bool SomeMethod();  
```  
  
 Pokud používáte tlbimp.exe k vytvoření `TestLib.dll` spravované knihovny bez zadání **/transform:dispret**, nástroj `SomeMethod` vytvoří následující `myTestLib.dll`podpis metody pro ve spravované knihovně .  
  
```csharp  
void SomeMethod(out bool x);  
```  
  
## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Tlbexp.exe (exportér knihovny typů)](tlbexp-exe-type-library-exporter.md)
- [Import knihovny typů ve formě sestavení](../interop/importing-a-type-library-as-an-assembly.md)
- [Souhrn převodu knihovny typů do sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Ildasm.exe (IL Disassembler)](ildasm-exe-il-disassembler.md)
- [Sn.exe (nástroj pro silný název)](sn-exe-strong-name-tool.md)
- [Sestavení se silným názvem](../../standard/assembly/strong-named.md)
- [Atributy pro import knihoven typů do interop sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y6a7ak23(v=vs.100))
- [Příkazové řádky](developer-command-prompt-for-vs.md)
