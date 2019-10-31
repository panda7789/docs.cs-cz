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
ms.openlocfilehash: fcbbc99c06e7c9666d58133bef20b84ef40c98d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104334"
---
# <a name="tlbimpexe-type-library-importer"></a>Tlbimp.exe (importér knihovny typů)
Nástroj Type Library Importer převádí definice typu nalezené v knihovně typů modelu COM na ekvivalentní definice v sestavení Common Language Runtime. Výstupem nástroje Tlbimp.exe je binární soubor (sestavení) obsahující metadata modulu runtime pro typy definované v rámci původní knihovny typů. Tento soubor můžete prozkoumávat pomocí nástrojů, jako je [Ildasm. exe](ildasm-exe-il-disassembler.md).  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
tlbimp tlbFile [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*tlbFile*|Název jakéhokoli souboru obsahujícího knihovnu typů modelu COM.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/asmversion:** *číslo_verze*|Určuje číslo verze vytvářeného sestavení. Ve formátu *hlavní_verze. podverze. sestavení. revize*zadejte číslo *versionNumber* .|  
|**/Company:** `companyinformation`|Přidá informace o společnosti do výstupního sestavení.|  
|**/Copyright:** `copyrightinformation`|Přidá informace o autorských právech do výstupního sestavení. Tyto informace lze zobrazit v dialogovém okně **vlastnosti souboru** pro sestavení.|  
|**/delaysign**|Říká nástroji Tlbimp.exe, aby podepsal výsledné sestavení se silným názvem pomocí zpožděného podepisování. Tuto možnost je nutné zadat buď pomocí možnosti **/keycontainer:** , **/keyfile:** , nebo **/PublicKey:** . Další informace o procesu opožděného podepisování naleznete v tématu [Zpožděné podepisování sestavení](../../standard/assembly/delay-sign.md).|  
|**/Help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/keycontainer:** *ContainerName*|Podepíše výsledné sestavení se silným názvem pomocí dvojice veřejného a privátního klíče nalezené v kontejneru klíčů určeném parametrem *ContainerName*.|  
|**/keyfile:** *název souboru*|Podepíše výsledné sestavení se silným názvem pomocí páru oficiálního veřejného/soukromého klíče vydavatele, který se nachází v *souboru filename*.|  
|**/Machine:** `machinetype`|Vytvoří sestavení určené pro konkrétní typ počítače (mikroprocesoru). Podporované typy počítačů: x86, x64, Itanium a Agnostic.|  
|**/Namespace:** *obor názvů*|Určuje obor názvů, ve kterém se má vytvořit sestavení.|  
|**/noclassmembers**|Zabraňuje nástroji Tlbimp.exe v přidávání členů do tříd. Tím se vyhnete potenciálním <xref:System.TypeLoadException>.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/out:** *filename*|Určuje název výstupního souboru, sestavení a oboru názvů, do kterých chcete zapsat definice metadat. Možnost **/out** nemá žádný vliv na obor názvů sestavení, pokud knihovna typů určuje vlastní atribut IDL (Interface Definition Language), který explicitně řídí obor názvů sestavení. Pokud tuto možnost nezadáte, nástroj Tlbimp.exe zapíše metadata do souboru se stejným názvem, jaký má skutečná knihovna typů definovaná v rámci vstupního souboru, a přiřadí mu příponu .dll. Pokud má výstupní soubor stejný název jako vstupní soubor, nástroj vygeneruje chybu bránící přepsání knihovny typů.|  
|**/primary**|Vytvoří primární sestavení zprostředkovatele komunikace pro zadanou knihovnu typů. Do sestavení jsou vloženy informace o tom, že toto sestavení vytvořil vydavatel knihovny typů. Zadáním primárního sestavení zprostředkovatele komunikace odlišíte sestavení vydavatele od ostatních sestavení vytvořených z knihovny typů používající nástroj Tlbimp.exe. Možnost **/Primary** byste měli použít pouze v případě, že jste vydavatel knihovny typů, kterou importujete pomocí nástroje Tlbimp. exe. Všimněte si, že je nutné podepsat primární definiční sestavení se [silným názvem](../../standard/assembly/strong-named.md). Další informace naleznete v tématu [primární spolupracující sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).|  
|**/Product:** `productinformation`|Přidá informace o produktu do výstupního sestavení. Tyto informace lze zobrazit v dialogovém okně **vlastnosti souboru** pro sestavení.|  
|**parametr/ProductVersion:** `productversioninformation`|Přidá informace o verzi produktu do výstupního sestavení. Neexistují žádná omezení formátu. Tyto informace lze zobrazit v dialogovém okně **vlastnosti souboru** pro sestavení.|  
|**/PublicKey:** *název souboru*|Určuje soubor obsahující veřejný klíč pro použití k podepsání výsledného sestavení. Zadáte-li možnost **/keyfile:** nebo **/keycontainer:** namísto **/PublicKey:** , nástroj Tlbimp. exe vygeneruje veřejný klíč z páru veřejného a privátního klíče dodaného s **/keyfile:** nebo **/keycontainer:** . Možnost **/PublicKey:** podporuje testovací klíč a scénáře pro zpožděné podepisování. Soubor má formát generovaný nástrojem Sn.exe. Další informace naleznete v tématu možnost **-p** programu sn. exe v [nástroji Strong Name (Sn. exe)](sn-exe-strong-name-tool.md).|  
|**/Reference:** *filename*|Určuje soubor sestavení, který se má použít při řešení odkazů na typy definované mimo aktuální knihovnu typů. Pokud nezadáte možnost **/reference** , nástroj Tlbimp. exe automaticky rekurzivně importuje všechny externí knihovny typů, na které se importovaná knihovna typů odkazuje. Zadáte-li možnost **/reference** , nástroj se pokusí přeložit externí typy v odkazovaných sestaveních předtím, než importuje jiné knihovny typů.|  
|**/Silence:** `warningnumber`|Potlačí zobrazení konkrétního upozornění. Tuto možnost nelze použít s **/Silent**.|  
|**/Silent**|Potlačí zobrazování zpráv o úspěšném dokončení. Tuto možnost nelze použít s **/Silence**.|  
|**/strictref**|Neimportuje knihovnu typů, pokud nástroj nemůže vyřešit všechny odkazy v rámci aktuálního sestavení, sestavení určených s možností **/reference** nebo registrovaných primárních spolupracujících sestavení (PIA).|  
|**/strictref:nopia**|Stejné jako **/strictref**, ale ignoruje PIA.|  
|**/sysarray**|Určuje, že nástroj má importovat typ SafeArray ve stylu COM jako spravovaný typ <xref:System.Array>.|  
|**/tlbreference:** *název souboru*|Určuje soubor knihovny typů, který se má použít k vyřešení odkazů knihovny typů bez konzultace s registrem.<br /><br /> Tato možnost nenačte některé starší formáty knihovny typů.  Stále však můžete načíst starší formáty knihovny typů implicitně pomocí registru nebo aktuálního adresáře.|  
|**/Trademark:** `trademarkinformation`|Přidá informace o obchodní známce do výstupního sestavení. Tyto informace lze zobrazit v dialogovém okně **vlastnosti souboru** pro sestavení.|  
|**/Transform:** *deformace*|Transformuje metadata, jak jsou určena parametrem *Transform* .<br /><br /> Zadejte **dispret** pro parametr Transformed pro transformaci [out, retval *] parametrů metod* na rozhraních jenom pro odesílání (IDispatch) na návratové hodnoty.<br /><br /> Další informace o této možnosti naleznete v příkladech dále v tomto tématu.|  
|**/UNSAFE**|Vytvoří rozhraní bez kontroly zabezpečení rozhraní .NET Framework. Volání metody, která je vystavena tímto způsobem, může představovat bezpečnostní riziko. Tuto možnost nepoužívejte, pokud si nejste vědomi rizika vystavení takového kódu.|  
|**/verbose**|Určuje režim podrobného vypisování; zobrazí další informace o importované knihovně typů.|  
|**/VariantBoolFieldToBool**|Převede pole `VARIANT_BOOL` ve strukturách na <xref:System.Boolean>.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
> [!NOTE]
> Možnosti příkazového řádku pro nástroj Tlbimp.exe nerozlišují malá a velká písmena a lze je zadat v libovolném pořadí. Pro jednoznačnou identifikaci je potřeba pouze poskytnout dostatek parametrů. Proto **/n** je ekvivalentem **/nologo** a **/ou:** *soubor. dll souboru. dll* je ekvivalentem **/out:** soubor *. dll*.  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Tlbimp.exe provádí převody celé knihovny typů najednou. Pomocí tohoto nástroje nelze generovat informace pro podmnožinu typů definovaných v rámci jedné knihovny typů.  
  
 Je často užitečné nebo nutné, aby bylo možné přiřadit [silné názvy](../../standard/assembly/strong-named.md) sestavením. Proto nástroj Tlbimp.exe obsahuje možnosti pro poskytnutí informací nezbytných k vytvoření sestavení se silným názvem. Parametry **/keyfile:** a **/keycontainer:** Podepište sestavení se silnými názvy. Je tedy logické zadat vždy pouze jednu z těchto možností.  
  
 Více referenčních sestavení můžete zadat několikrát pomocí možnosti **/reference** .
 
 V důsledku způsobu, jakým nástroj Tlbimp. exe generuje sestavení, není možné změnit cílení na sestavení na jinou verzi `mscorlib`. Například pokud si přejete vygenerovat sestavení, které cílí na .NET Framework 2,0, je nutné použít nástroj Tlbimp. exe dodaný s .NET Framework 2.0/3.0/3.5 SDK. Aby bylo možné cílit .NET Framework 4. x, je třeba použít nástroj Tlbimp. exe dodaný pomocí sady .NET Framework 4. x SDK.
 
 ID prostředku lze volitelně připojit k souboru knihovny typů při importu knihovny typů z modulu obsahujícího více knihoven typů. Nástroj Tlbimp.exe je schopen najít tento soubor pouze v případě, že se nachází v aktuálním adresáři, nebo pokud zadáte úplnou cestu. Podívejte se na příklad dále v tomto tématu.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz vygeneruje sestavení se stejným názvem, jako má knihovna typů nalezené v `myTest.tlb` a s příponou. dll.  
  
```console  
tlbimp myTest.tlb   
```  
  
 Následující příkaz vygeneruje sestavení s názvem `myTest.dll`.  
  
```console  
tlbimp  myTest.tlb  /out:myTest.dll  
```  
  
 Následující příkaz vygeneruje sestavení se stejným názvem, jako má knihovna typů určená `MyModule.dll\1` a s příponou. dll. `MyModule.dll\1` se musí nacházet v aktuálním adresáři.  
  
```console  
tlbimp MyModule.dll\1  
```  
  
 Následující příkaz vygeneruje sestavení s názvem `myTestLib.dll` pro `TestLib.dll`knihovny typů. Možnost **/Transform: dispret** transformuje jakékoli parametry [out, retval] metod na IDispatch v knihovně typů na vrácené hodnoty ve spravované knihovně.  
  
```console  
tlbimp TestLib.dll /transform:dispret /out:myTestLib.dll  
```  
  
 Knihovna typů `TestLib.dll`v předchozím příkladu obsahuje metodu odesílajícího názvu `SomeMethod`, která vrací void a má parametr [out, retval]. Následující kód je podpis metody vstupní knihovny typů pro `SomeMethod` v `TestLib.dll`.  
  
```cpp  
void SomeMethod([out, retval] VARIANT_BOOL*);  
```  
  
 Pokud zadáte možnost **/Transform: dispret** , nástroj Tlbimp. exe převede parametr `[out, retval]` `SomeMethod` na návratovou hodnotu `bool`. Následuje signatura metody, kterou nástroj Tlbimp. exe generuje pro `SomeMethod` ve spravované knihovně `myTestLib.dll` při zadání možnosti **/Transform: dispret** .  
  
```csharp  
bool SomeMethod();  
```  
  
 Použijete-li nástroj Tlbimp. exe k vytvoření spravované knihovny pro `TestLib.dll` bez zadání parametru **/Transform: dispret**, nástroj vytvoří následující signaturu metody pro `SomeMethod` v `myTestLib.dll`spravované knihovny.  
  
```csharp  
void SomeMethod(out bool x);  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](index.md)
- [Tlbexp.exe (exportér knihovny typů)](tlbexp-exe-type-library-exporter.md)
- [Import knihovny typů ve formě sestavení](../interop/importing-a-type-library-as-an-assembly.md)
- [Souhrn převodu knihovny typů na sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Ildasm.exe (IL Disassembler)](ildasm-exe-il-disassembler.md)
- [Sn.exe (nástroj pro silný název)](sn-exe-strong-name-tool.md)
- [Sestavení se silným názvem](../../standard/assembly/strong-named.md)
- [Atributy pro import knihoven typů do sestavení Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y6a7ak23(v=vs.100))
- [Příkazové řádky](developer-command-prompt-for-vs.md)
