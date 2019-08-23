---
title: Sn.exe (nástroj pro silný název)
ms.date: 03/30/2017
helpviewer_keywords:
- public keys, signing files
- Strong Name tool
- Sn.exe
- assemblies [.NET Framework], signing
- signing files
- strong-named assemblies, signing files
- key pairs for signing files
ms.assetid: c1d2b532-1b8e-4c7a-8ac5-53b801135ec6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35e89584f3916d748809960d33a31eb4e8fb9c6a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938021"
---
# <a name="snexe-strong-name-tool"></a>Sn.exe (nástroj pro silný název)
Nástroj Strong Name (Sn. exe) pomáhá podepisovat sestavení se [silnými názvy](../../../docs/framework/app-domains/strong-named-assemblies.md). Nástroj Sn.exe poskytuje možnosti pro správu klíčů, generování podpisů a ověřování podpisů.  
  
> [!WARNING]
> Nespoléhá se na silné názvy zabezpečení. Poskytují pouze jedinečnou identitu.

 Další informace o silných názvech a sestaveních se silným názvem naleznete v tématu sestavení [se silným [názvem](../../../docs/framework/app-domains/strong-named-assemblies.md) a postupy: Podepište sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 Nástroj Strong Name je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  

> [!NOTE]
> Na 64 počítačů 32 spusťte 64bitovou verzi programu sn. exe pomocí Developer Command Prompt pro sadu Visual Studio a verzi 64-bit pomocí příkazového řádku sady Visual Studio x64 win64. 
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sn [-quiet][option [parameter(s)]]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|**-a** *identityKeyPairFile* *signaturePublicKeyFile*|Vygeneruje <xref:System.Reflection.AssemblySignatureKeyAttribute> data pro migraci klíče identity na podpisový klíč ze souboru.|  
|**-ac** *identityPublicKeyFile* *identityKeyPairContainer* *signaturePublicKeyFile*|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> data pro migraci klíče identity na podpisový klíč z kontejneru klíčů.|  
|**-c** [*CSP*]|Nastaví výchozího zprostředkovatele kryptografických služeb (CSP) pro použití k podepisování se silným názvem. Toto nastavení platí pro celý počítač. Pokud název CSP nezadáte, nástroj Sn.exe vymaže aktuální nastavení.|  
|**– d** *kontejner*|Odstraní zadaný kontejner klíče z CSP silného názvu.|  
|**-D**  *assembly1 assembly2*|Ověří, zda se dvě sestavení liší pouze v podpisu. Toto se často používá jako kontrola poté, co bylo sestavení znovu podepsáno jiným párem klíčů.|  
|**-e**  *outfile sestavení*|Extrahuje veřejný klíč ze *sestavení* a uloží jej do *souboru.*|  
|**-h**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**– i** *kontejner InFile*|Nainstaluje dvojici klíčů ze *souboru InFile* v zadaném kontejneru klíčů. Kontejner klíčů je umístěn v CSP silného názvu.|  
|**– k** [*Velikost písma*] *soubor* .|Vygeneruje nový <xref:System.Security.Cryptography.RSACryptoServiceProvider> klíč o zadané velikosti a zapíše ho do zadaného souboru.  Do souboru je zapsán veřejný i soukromý klíč.<br /><br /> Nezadáte-li velikost klíče, je dle výchozího nastavení vygenerován 1024bitový klíč, pokud máte nainstalovaný vylepšený zprostředkovatel kryptografických služeb Microsoft. V opačném případě je vygenerován 512bitový klíč.<br /><br /> Parametr *Size* klíče podporuje délky klíčů od 384 do 16 384 bitů v přírůstcích po 8 bitech, pokud máte nainstalovaného rozšířeného zprostředkovatele kryptografických služeb společnosti Microsoft.  Je-li nainstalován základní zprostředkovatel kryptografických služeb Microsoft, podporuje délky klíčů od 384 do 512 bitů v krocích po 8 bitech.|  
|**-m** [**y** *&#124;* **n**]|Určí, zda jsou kontejnery klíčů specifické pro počítač nebo pro uživatele. Pokud zadáte *y*, kontejnery klíčů jsou specifické pro počítač. Pokud zadáte *n*, kontejnery klíčů jsou specifické pro uživatele.<br /><br /> Není-li zadána žádná z hodnot y nebo n, zobrazí tato možnost aktuální nastavení.|  
|**-o**  *infile* [*outfile*]|Extrahuje veřejný klíč ze *souboru InFile* a uloží jej do souboru. csv. Každý bajt veřejného klíče je oddělen čárkou. Tento formát je užitečný pro pevné zakódování odkazů na klíče jako inicializovaných polí ve zdrojovém kódu. Pokud nezadáte žádný *soubor*, tato možnost umístí výstup do schránky. **Poznámka:**  Tato možnost neověřuje, zda je vstupem pouze veřejný klíč. `infile` Pokud obsahuje dvojici klíčů s privátním klíčem, je také extrahován soukromý klíč.|  
|**-p** soubor. [*hashAlg*]|Extrahuje veřejný klíč z páru klíčů v *souboru InFile* a uloží jej do *souboru*s možností volitelně pomocí algoritmu RSA určeného parametrem *hashAlg*. Tento veřejný klíč lze použít k zpožděnému podepsání sestavení pomocí možností **/delaysign +** a **/keyfile** [linkeru sestavení (Al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Pokud je sestavení podepsáno opožděně, je v době kompilace nastaven pouze veřejný klíč a v souboru je vyhrazen prostor pro pozdější přidání podpisu, až bude znám soukromý klíč.|  
|**-pc**  *kontejneru* *outfile* [*hashalg*]|Extrahuje veřejný klíč z páru klíčů v *kontejneru* a uloží jej do *souboru*. Použijete-li možnost *hashAlg* , použije se k extrakci veřejného klíče algoritmus RSA.|  
|**– PB** [**y** *&#124;* **n**]|Určí, zda bude vynucena zásada potlačení silných názvů. Zadáte-li hodnotu *y*, silné názvy pro sestavení s úplným vztahem důvěryhodnosti nejsou ověřovány, pokud <xref:System.AppDomain>jsou načteny do plně důvěryhodného vztahu důvěryhodnosti. Zadáte-li hodnotu *n*, silné názvy jsou ověřovány pro správnost, ale ne pro konkrétní silný název. <xref:System.Security.Permissions.StrongNameIdentityPermission> Nemá žádný vliv na sestavení s úplným vztahem důvěryhodnosti. Je zapotřebí provést vlastní kontrolu shody silných názvů.<br /><br /> `y` Pokudaninenízadán,zobrazí`n` Tato možnost aktuální nastavení. Výchozí hodnota je `y`. **Poznámka:**  Na 64bitových počítačích je zapotřebí tento parametr nastavit pro 32bitovou i 64bitovou instanci nástroje Sn.exe.|  
|**-q**[**uiet**]|Určuje použití tichého režimu; potlačí zobrazování zpráv o úspěchu.|  
|**-R**[**a**] *sestavení* *Vstupní_soubor*|Znovu podepíše dříve podepsané nebo zpožděné podepsané sestavení s dvojicí klíčů v *souboru InFile*.<br /><br /> Je **-li použito-RA** , jsou hodnoty hash přepočítány pro všechny soubory v sestavení.|  
|**-Rc**[**a**] *kontejneru sestavení*|Znovu podepíše dříve podepsané nebo zpožděné podepsané sestavení s dvojicí klíčů v *kontejneru*.<br /><br /> Je **-li použit-RCA** , jsou pro všechny soubory v sestavení přepočítány hodnoty hash.|  
|**– RH** *sestavení*|Přepočítá hodnoty hash pro všechny soubory v sestavení.|  
|**-t** [**p**] *InFile*|Zobrazí token pro veřejný klíč uložený v *souboru InFile*. Obsah *souboru InFile* musí být veřejný klíč dříve vygenerovaný ze souboru dvojice klíčů pomocí **-p**.  Nepoužívejte možnost **-t [p]** k extrakci tokenu přímo ze souboru dvojice klíčů.<br /><br /> Nástroj Sn.exe počítá token z veřejného klíče pomocí funkce hash. Z důvodu šetření místem ukládá modul CLR tokeny veřejných klíčů do manifestů jako součást odkazů na jiné sestavení ve chvíli, kdy je do sestavení se silným názvem zaznamenána závislost. Možnost **-TP** zobrazí spolu s tokenem také veřejný klíč. Pokud byl <xref:System.Reflection.AssemblySignatureKeyAttribute> atribut použit na sestavení, je token pro klíč identity a je zobrazen název algoritmu hash a klíč identity.<br /><br /> Tato možnost neověřuje popis sestavení a neměla by být použita pro rozhodování o důvěryhodnosti.  Tato možnost zobrazuje pouze nezpracovaná data tokenu veřejného klíče.|  
|**-T** *sestavení* [**p**]|Zobrazí token veřejného klíče pro *sestavení.* *Sestavení* musí být název souboru, který obsahuje manifest sestavení.<br /><br /> Nástroj Sn.exe počítá token z veřejného klíče pomocí funkce hash. Z důvodu šetření místem ukládá modul runtime tokeny veřejných klíčů do manifestů jako součást odkazů na jiné sestavení ve chvíli, kdy je do sestavení se silným názvem zaznamenána závislost. Možnost **-TP** zobrazí spolu s tokenem také veřejný klíč. Pokud byl <xref:System.Reflection.AssemblySignatureKeyAttribute> atribut použit na sestavení, je token pro klíč identity a je zobrazen název algoritmu hash a klíč identity.<br /><br /> Tato možnost neověřuje popis sestavení a neměla by být použita pro rozhodování o důvěryhodnosti.  Tato možnost zobrazuje pouze nezpracovaná data tokenu veřejného klíče.|  
|`-TS` `assembly` `infile`|Otestuje podpis podepsaného nebo částečně podepsaného `assembly` pomocí páru klíčů v. `infile`|  
|-`TSc` `assembly` `container`|Otestuje podpis podepsaného nebo částečně podepsaného `assembly` pomocí páru klíčů v kontejneru `container`klíčů.|  
|**-v** *sestavení*|Ověří silný název v *sestavení*, kde *sestavení* je název souboru, který obsahuje manifest sestavení.|  
|**-vf**  *sestavení*|Ověří silný název v *sestavení.* Na rozdíl od možnosti- **v** **– VF** vynutí ověření, i když je zakázaný pomocí možnosti **-VR** .|  
|**-Vk**  *regfile.reg* *sestavení* [*userlist*] [*infile*]|Vytvoří soubor registračních položek (.reg), které lze použít k registraci zadaného sestavení pro vynechání ověření. Pravidla pro pojmenování sestavení, která platí pro možnost **-VR** , se vztahují také na **– VK** . Informace o možnostech *userlist* a InFile najdete v tématu – možnost **– VR** .|  
|**-Vl**|Vypíše aktuální nastavení pro ověřování silných názvů v tomto počítači.|  
|**-Vr**  *sestavení* [*userlist*] [*infile*]|Zaregistruje *sestavení* pro vynechání ověření. Volitelně lze také zadat čárkou oddělený seznam uživatelských jmen, pro která by vynechání ověřování mělo platit. Pokud zadáte *soubor InFile*, ověřování zůstane zapnuto, ale veřejný klíč v *souboru InFile* se používá v operacích ověřování. Můžete zadat *sestavení* ve formuláři  *\*, StrongName* pro registraci všech sestavení se zadaným silným názvem. Pro *StrongName*zadejte řetězec šestnáctkových číslic, který představuje tokenový tvar veřejného klíče. Chcete-li zobrazit token veřejného klíče, Prohlédněte si možnosti **-t** a **-t** . **Upozornění**  Tuto možnost používejte pouze během vývoje. Přidání sestavení na seznam pro přeskočení ověření vytvoří ohrožení zabezpečení. Škodlivé sestavení by mohlo použít plně zadaný název sestavení (název sestavení, verze, jazyková verze a token veřejného klíče), které je přidáno do seznamu pro přeskočení ověření, k falšování identity. To by také umožnilo škodlivému sestavení přeskočit ověření.|  
|||  
|**-Vu**  *sestavení*|Zruší registraci *sestavení* pro vynechání ověření. Stejná pravidla pro pojmenovávání sestavení, která se vztahují na **VR** , se vztahují na **VU**.|  
|**-Vx**|Odstraní všechny záznamy o vynechání ověřování.|  
|**-?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
> [!NOTE]
> Všechny možnosti nástroje Sn.exe rozlišují velká a malá písmena a musí být pro rozpoznání nástrojem zapsána přesně dle tabulky.  
  
## <a name="remarks"></a>Poznámky  
 Možnosti **-R** a **– RC** jsou užitečné u sestavení, která byla podepsána opožděně. V tomto scénáři byl při kompilování nastaven pouze veřejný klíč a podepsání bylo provedeno později, až při znalosti soukromého klíče.  
  
> [!NOTE]
> Pro parametry (například –**VR)** , které zapisují do chráněných prostředků, jako je například registr, spusťte nástroj Sn. exe jako správce.  
  
Nástroj Strong Name předpokládá, že páry veřejného a privátního klíče jsou vygenerovány pomocí `AT_SIGNATURE` identifikátoru algoritmu. Páry veřejného a privátního klíče generované `AT_KEYEXCHANGE` algoritmem generují chybu. 

## <a name="examples"></a>Příklady  
 Následující příkaz vytvoří nový, náhodný pár klíčů a uloží jej do `keyPair.snk`.  
  
```  
sn -k keyPair.snk  
```  
  
 Následující příkaz uloží klíč `keyPair.snk` do kontejneru `MyContainer` v rámci zprostředkovatele CSP se silným názvem.  
  
```  
sn -i keyPair.snk MyContainer  
```  
  
 Následující příkaz extrahuje veřejný klíč z `keyPair.snk` a uloží jej do. `publicKey.snk`  
  
```  
sn -p keyPair.snk publicKey.snk  
```  
  
 Následující příkaz zobrazí veřejný klíč a token pro veřejný klíč obsažený v `publicKey.snk`.  
  
```  
sn -tp publicKey.snk  
```  
  
 Následující příkaz ověří sestavení `MyAsm.dll`.  
  
```  
sn -v MyAsm.dll  
```  
  
 Následující příkaz odstraní `MyContainer` z výchozího zprostředkovatele CSP.  
  
```  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
