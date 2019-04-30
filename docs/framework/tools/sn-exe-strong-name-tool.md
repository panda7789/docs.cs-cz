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
ms.openlocfilehash: 24a8c7ce090b286db9d86e0fc6c54ae33e7e2d5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61919500"
---
# <a name="snexe-strong-name-tool"></a>Sn.exe (nástroj pro silný název)
Nástroj Strong Name (Sn.exe) pomáhá podepsat sestavení se [silných názvů](../../../docs/framework/app-domains/strong-named-assemblies.md). Nástroj Sn.exe poskytuje možnosti pro správu klíčů, generování podpisů a ověřování podpisů.  
  
> [!WARNING]
> Nespoléhejte na silných názvů pro zabezpečení. Poskytují jedinečné identity.

 Další informace o silné názvy a sestavení se silným názvem naleznete v tématu [sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md) a [jak: Podepsání sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 Nástroj Strong Name je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  

> [!NOTE]
>  Na 64bitových počítačích spusťte 32bitovou verzi nástroje Sn.exe pomocí příkazového řádku pro vývojáře pro Visual Studio a 64bitovou verzi pomocí příkazového řádku sady Visual Studio x64 Win64. 
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sn [-quiet][option [parameter(s)]]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|**-a** *identityKeyPairFile* *signaturePublicKeyFile*|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> dat k migraci klíče identity na klíč podpisu ze souboru.|  
|**-ac** *identityPublicKeyFile* *identityKeyPairContainer* *signaturePublicKeyFile*|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> dat k migraci klíče identity na klíč podpisu z kontejneru klíčů.|  
|**-c** [*csp*]|Nastaví výchozího zprostředkovatele kryptografických služeb (CSP) pro použití k podepisování se silným názvem. Toto nastavení platí pro celý počítač. Pokud název CSP nezadáte, nástroj Sn.exe vymaže aktuální nastavení.|  
|**-d** *kontejneru*|Odstraní zadaný kontejner klíče z CSP silného názvu.|  
|**-D**  *assembly1 assembly2*|Ověří, zda se dvě sestavení liší pouze v podpisu. Toto se často používá jako kontrola poté, co bylo sestavení znovu podepsáno jiným párem klíčů.|  
|**-e**  *outfile sestavení*|Extrahuje veřejný klíč z *sestavení* a uloží jej do *outfile.*|  
|**-h**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**-i** *infile kontejneru*|Nainstaluje pár klíčů ze *infile* do zadaného kontejneru klíčů. Kontejner klíčů je umístěn v CSP silného názvu.|  
|**-k** [*keysize*] *outfile*|Vygeneruje nový <xref:System.Security.Cryptography.RSACryptoServiceProvider> klíče zadané velikosti a zapíše jej do zadaného souboru.  Do souboru je zapsán veřejný i soukromý klíč.<br /><br /> Nezadáte-li velikost klíče, je dle výchozího nastavení vygenerován 1024bitový klíč, pokud máte nainstalovaný vylepšený zprostředkovatel kryptografických služeb Microsoft. V opačném případě je vygenerován 512bitový klíč.<br /><br /> *Keysize* parametr podporuje délky klíčů od 384 do 16384 bitů v krocích po 8 bitech, pokud máte Vylepšený zprostředkovatel kryptografických služeb Microsoft nainstalována.  Je-li nainstalován základní zprostředkovatel kryptografických služeb Microsoft, podporuje délky klíčů od 384 do 512 bitů v krocích po 8 bitech.|  
|**-m** [**y** *&#124;* **n**]|Určí, zda jsou kontejnery klíčů specifické pro počítač nebo pro uživatele. Pokud zadáte *y*, jsou kontejnery specifické pro počítač. Pokud zadáte *n*, jsou kontejnery specifické pro uživatele.<br /><br /> Není-li zadána žádná z hodnot y nebo n, zobrazí tato možnost aktuální nastavení.|  
|**-o**  *infile* [*outfile*]|Extrahuje veřejný klíč z *infile* a uloží jej do souboru .csv. Každý bajt veřejného klíče je oddělen čárkou. Tento formát je užitečný pro pevné zakódování odkazů na klíče jako inicializovaných polí ve zdrojovém kódu. Pokud nezadáte *outfile*, tato možnost umístí výstup do schránky. **Poznámka:**  Tato možnost neověřuje, zda je vstupem pouze veřejný klíč. Pokud `infile` obsahuje pár klíčů se soukromým klíčem, je privátní klíč také extrahován.|  
|**-p** *infile outfile* [*hashalg*]|Extrahuje veřejný klíč z páru klíčů v *infile* a uloží jej do *outfile*, volitelně pomocí algoritmus RSA zadaný parametrem *hashalg*. Tento veřejný klíč lze použít pro opožděný podpis sestavení pomocí **/delaysign+** a **/keyfile** možnosti, které [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Pokud je sestavení podepsáno opožděně, je v době kompilace nastaven pouze veřejný klíč a v souboru je vyhrazen prostor pro pozdější přidání podpisu, až bude znám soukromý klíč.|  
|**-pc**  *kontejneru* *outfile* [*hashalg*]|Extrahuje veřejný klíč z páru klíčů v *kontejneru* a uloží jej do *outfile*. Pokud používáte *hashalg* možnost algoritmus RSA slouží k extrakci veřejného klíče.|  
|**-Pb** [**y** *&#124;* **n**]|Určí, zda bude vynucena zásada potlačení silných názvů. Pokud zadáte *y*, silné názvy sestavení s úplnou důvěryhodností pořadí úloh se neověřuje při načtení do plné důvěryhodnosti <xref:System.AppDomain>. Pokud zadáte *n*, silných názvů se ověří správnost, ale ne pro konkrétní silný název. <xref:System.Security.Permissions.StrongNameIdentityPermission> Nemá žádný vliv na sestavení s úplnou důvěryhodností. Je zapotřebí provést vlastní kontrolu shody silných názvů.<br /><br /> Pokud ani `y` ani `n` není zadán, zobrazí tato možnost aktuální nastavení. Výchozí hodnota je `y`. **Poznámka:**  Na 64bitových počítačích je zapotřebí tento parametr nastavit pro 32bitovou i 64bitovou instanci nástroje Sn.exe.|  
|**-q**[**uiet**]|Určuje použití tichého režimu; potlačí zobrazování zpráv o úspěchu.|  
|**-R**[**a**] *sestavení* *Vstupní_soubor*|Znovu podepíše dříve nebo opožděně podepsané sestavení párem klíčů v *infile*.<br /><br /> Pokud **-Ra** se používá, pro všechny soubory v sestavení jsou přepočítány hodnoty hash.|  
|**-Rc**[**a**] *kontejneru sestavení*|Znovu podepíše dříve nebo opožděně podepsané sestavení párem klíčů v *kontejneru*.<br /><br /> Pokud **– analýza Rca** se používá, pro všechny soubory v sestavení jsou přepočítány hodnoty hash.|  
|**-Rh** *sestavení*|Přepočítá hodnoty hash pro všechny soubory v sestavení.|  
|**-t**[**p**] *infile*|Zobrazí token pro veřejný klíč uložený ve *infile*. Obsah *infile* musí být veřejný klíč dříve vygenerovaný z páru klíčů pomocí souboru **-p**.  Nepoužívejte **-t [p]** možnost extrahovat token přímo ze souboru páru klíčů.<br /><br /> Nástroj Sn.exe počítá token z veřejného klíče pomocí funkce hash. Z důvodu šetření místem ukládá modul CLR tokeny veřejných klíčů do manifestů jako součást odkazů na jiné sestavení ve chvíli, kdy je do sestavení se silným názvem zaznamenána závislost. **- Tp** možnost se zobrazí spolu s tokenem také veřejný klíč. Pokud <xref:System.Reflection.AssemblySignatureKeyAttribute> atributu byl použit k sestavení, je token klíči identity a zobrazí se název hashovacího algoritmu a klíč identity.<br /><br /> Tato možnost neověřuje popis sestavení a neměla by být použita pro rozhodování o důvěryhodnosti.  Tato možnost zobrazuje pouze nezpracovaná data tokenu veřejného klíče.|  
|**-T**[**p**] *sestavení*|Zobrazí token veřejného klíče pro *sestavení.* *Sestavení* musí být název souboru obsahujícího manifest sestavení.<br /><br /> Nástroj Sn.exe počítá token z veřejného klíče pomocí funkce hash. Z důvodu šetření místem ukládá modul runtime tokeny veřejných klíčů do manifestů jako součást odkazů na jiné sestavení ve chvíli, kdy je do sestavení se silným názvem zaznamenána závislost. **- Tp** možnost se zobrazí spolu s tokenem také veřejný klíč. Pokud <xref:System.Reflection.AssemblySignatureKeyAttribute> atributu byl použit k sestavení, je token klíči identity a zobrazí se název hashovacího algoritmu a klíč identity.<br /><br /> Tato možnost neověřuje popis sestavení a neměla by být použita pro rozhodování o důvěryhodnosti.  Tato možnost zobrazuje pouze nezpracovaná data tokenu veřejného klíče.|  
|`-TS` `assembly` `infile`|Vyzkouší podepsaného nebo částečně podepsaného `assembly` párem klíčů v `infile`.|  
|-`TSc` `assembly` `container`|Vyzkouší podepsaného nebo částečně podepsaného `assembly` párem klíčů v kontejneru klíčů `container`.|  
|**-v** *sestavení*|Ověří silný název v *sestavení*, kde *sestavení* je název souboru obsahujícího manifest sestavení.|  
|**-vf**  *sestavení*|Ověří silný název v *sestavení.* Na rozdíl od **- v** možnost **-vf** vynutí ověření i v případě, že je zakázané, pomocí **- Vr** možnost.|  
|**-Vk**  *regfile.reg* *sestavení* [*userlist*] [*infile*]|Vytvoří soubor registračních položek (.reg), které lze použít k registraci zadaného sestavení pro vynechání ověření. Pravidla pojmenovávání sestavení, které se vztahují **- Vr** možnost použít **– Vk** také. Informace o *userlist* a *infile* možnosti, najdete v článku **– Vr** možnost.|  
|**-Vl**|Vypíše aktuální nastavení pro ověřování silných názvů v tomto počítači.|  
|**-Vr**  *sestavení* [*userlist*] [*infile*]|Zaregistruje *sestavení* pro přeskočení ověření. Volitelně lze také zadat čárkou oddělený seznam uživatelských jmen, pro která by vynechání ověřování mělo platit. Pokud zadáte *infile*, zůstane ověřování povoleno, ale veřejný klíč v *infile* je použit. Můžete zadat *sestavení* ve formě  *\*, strongname* zaregistrovat všechna sestavení se zadaným silným názvem. Pro *strongname*, zadejte řetězec šestnáctkových číslic představující tokenizovanou formu veřejného klíče. Zobrazit **-t** a **-T** možnosti Zobrazit token veřejného klíče. **Upozornění:**  Tuto možnost používejte pouze během vývoje. Přidání sestavení na seznam pro přeskočení ověření vytvoří ohrožení zabezpečení. Škodlivé sestavení by mohlo použít plně zadaný název sestavení (název sestavení, verze, jazyková verze a token veřejného klíče), které je přidáno do seznamu pro přeskočení ověření, k falšování identity. To by také umožnilo škodlivému sestavení přeskočit ověření.|  
|||  
|**-Vu**  *sestavení*|Zruší registraci *sestavení* pro přeskočení ověření. Pravidla pojmenovávání sestavení platná pro **- Vr** platí pro **- Vu**.|  
|**-Vx**|Odstraní všechny záznamy o vynechání ověřování.|  
|**-?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
> [!NOTE]
>  Všechny možnosti nástroje Sn.exe rozlišují velká a malá písmena a musí být pro rozpoznání nástrojem zapsána přesně dle tabulky.  
  
## <a name="remarks"></a>Poznámky  
 **-R** a **– Rc** možnosti jsou užitečné se sestaveními, která se zpožděným podpisem. V tomto scénáři byl při kompilování nastaven pouze veřejný klíč a podepsání bylo provedeno později, až při znalosti soukromého klíče.  
  
> [!NOTE]
>  Pro parametry (například –**Vr)** zapisující do chráněných prostředků, jako je například registru, spusťte SN.exe jako správce.  
  
Nástroj Strong Name se předpokládá, že se vygenerují se klíče dvojice veřejného/soukromého `AT_SIGNATURE` identifikátor algoritmu. Veřejného/soukromého klíče dvojice generuje s použitím `AT_KEYEXCHANGE` algoritmus vygenerují chybu. 

## <a name="examples"></a>Příklady  
 Následující příkaz vytvoří nový, náhodný pár klíčů a uloží jej do `keyPair.snk`.  
  
```  
sn -k keyPair.snk  
```  
  
 Následující příkaz uloží klíč v `keyPair.snk` v kontejneru `MyContainer` v silného název zprostředkovatele kryptografických služeb.  
  
```  
sn -i keyPair.snk MyContainer  
```  
  
 Následující příkaz extrahuje veřejný klíč z `keyPair.snk` a uloží jej do `publicKey.snk`.  
  
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
  
 Následující příkaz odstraní `MyContainer` z výchozího CSP.  
  
```  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
