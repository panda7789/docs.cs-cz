---
title: Peverify.exe (nástroj PEVerify)
ms.date: 03/30/2017
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ae36736ac7174ff7f77ae5bba45e1fd3880169c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43538362"
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (nástroj PEVerify)
Nástroj PEVerify pomáhá vývojářům generujícím Microsoft Intermediate Language (MSIL) (například autorům kompilátorů a vývojářům skriptovacích modulů) zjistit, zda jejich kód MSIL a přidružená metadata splňují požadavky na bezpečnost typů. Některé kompilátory generují kód ověřitelně bezpečného typu pouze tehdy, když se vyhnete určitým jazykovým konstrukcím. Pokud jako vývojář používáte takový kompilátor, můžete chtít ověřit, že nebyla ohrožena bezpečnost typů vašeho kódu. V této situaci můžete spustit nástroj PEVerify pro soubory ke kontrole jazyka MSIL a metadat.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
peverify filename [options]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*Název souboru*|Přenosný spustitelný soubor (PE), pro který chcete zkontrolovat jazyk MSIL a metadata.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/ přerušit =** *maxErrorCount*|Přeruší ověřování po *maxErrorCount* chyby.<br /><br /> Tento parametr není podporován v rozhraní .NET Framework verze 2.0 a vyšší.|  
|**/Clock**|Změří a oznámí následující časy ověření v milisekundách:<br /><br /> **MD Val. cycle**<br /> Cyklus ověření metadat<br /><br /> **MD Val. pure**<br /> Čisté ověření metadat<br /><br /> **IL Ver. cycle**<br /> Cyklus ověřování Microsoft Intermediate Language (MSIL)<br /><br /> **IL Ver pure**<br /> Čisté ověřování MSIL<br /><br /> **MD Val. cycle** a **IL Ver. cycle** časy zahrnují čas potřebný k provedení potřebné procedur spuštění a vypnutí. **MD Val. pure** a **IL Ver pure** časy odrážet čas potřebný k provedení ověření nebo jenom k ověření.|  
|**/ Help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/HRESULT**|Zobrazí kódy chyb v šestnáctkovém formátu.|  
|**/ Ignorovat =** *hex.code* [, *hex.code*]|Ignoruje zadané kódy chyb.|  
|**/ Ignorovat = @** *responseFile*|Ignoruje kódy chyb uvedené v zadaném souboru odpovědí.|  
|**/IL**|Provádí kontroly ověření bezpečnosti typů jazyka MSIL pro metody implementované v sestavení určeném parametrem *filename*. Nástroj Vrátí podrobný popis každého nalezeného problému, pokud zadáte **/quiet** možnost.|  
|**/md**|Provádí kontroly ověřování metadat na sestavení určeném parametrem *filename*. Prochází kompletní strukturu metadat v souboru a hlásí všechny zaznamenané problémy s ověřením.|  
|**/nologo**|Potlačí zobrazení informací o verzi a autorských právech produktu.|  
|**/nosymbols**|V rozhraní .NET Framework verze 2.0 potlačí zobrazování čísel řádků z důvodu zpětné kompatibility.|  
|**/quiet**|Nastaví tichý režim; potlačí výstup hlášení problémů ověření. Nástroj Peverify.exe stále hlásí, zda je soubor typově bezpečný, ale již nehlásí informace o problémech, které brání v ověření bezpečnosti typu.|  
|`/transparent`|Ověří pouze transparentní metody.|  
|**/ Jedinečný**|Ignoruje opakující se kódy chyb.|  
|**/verbose**|V rozhraní .NET Framework verze 2.0 zobrazí další informace ve zprávách ověření MSIL.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Modul Common Language Runtime se opírá o typově bezpečné spuštění kódu aplikace k podpoře vynucení bezpečnostních a izolačních mechanismů. Za normálních okolností kód, který není [ověřitelně bezpečnost typů](https://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc) nelze spustit, nicméně můžete nastavit zásady zabezpečení umožňující spuštění důvěryhodného ale neověřitelný kód.  
  
 Pokud ani **/md** ani **/il** jsou zadány možnosti, Peverify.exe provede oba typy kontrol. PEVerify.exe provádí **/md** nejprve. Pokud zde nejsou žádné chyby **/il** kontroly jsou prováděny. Pokud zadáte obě **/md** a **/il**, **/il** kontroly jsou prováděny, i když nejsou chyby v metadatech. Proto, pokud nejsou žádné chyby metadat **peverify** *filename* je ekvivalentní **peverify** *filename* **/md** **/il**.  
  
 Nástroj Peverify.exe provádí komplexní kontroly MSIL u platných metadat na základě analýzy datového toku a seznamu několika stovek pravidel. Podrobné informace o kontrolách Peverify.exe provádí, podívejte se "specifikace ověřování metadat" a "MSIL specifikace sady instrukcí" ve složce Tools Developers Guide v [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
 Všimněte si, že rozhraní .NET Framework verze 2.0 nebo novější podporuje ověřitelné `byref` zadané pomocí následujících instrukcí jazyka MSIL: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` a `unbox`.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz provede ověření metadat a kontrolu bezpečnosti typů jazyka MSIL pro metody implementované v sestavení `myAssembly.exe`.  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 Po úspěšném dokončení výše uvedeného požadavku nástroj Peverify.exe zobrazí následující zprávu.  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 Následující příkaz provede ověření metadat a kontrolu bezpečnosti typů jazyka MSIL pro metody implementované v sestavení `myAssembly.exe`. Nástroj zobrazí čas potřebný k provedení těchto kontrol.  
  
```  
peverify myAssembly.exe /md /il /clock  
```  
  
 Po úspěšném dokončení výše uvedeného požadavku nástroj Peverify.exe zobrazí následující zprávu.  
  
```  
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 Následující příkaz provede ověření metadat a kontrolu bezpečnosti typů jazyka MSIL pro metody implementované v sestavení `myAssembly.exe`. Nástroj Peverify.exe se však zastaví, jakmile dosáhne maximálního počtu 100 chyb. Tento nástroj rovněž ignoruje zadané kódy chyb.  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 Následující příkaz vytvoří stejný výsledek jako předchozí příklad výše, ale Určuje kódy chyb v souboru odpovědí `ignoreErrors.rsp`.  
  
```  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 Soubor odpovědí může obsahovat seznam kódů chyb oddělených čárkami.  
  
```  
0x12345678, 0xABCD1234  
```  
  
 Soubor odpovědí lze také naformátovat s jedním kódem chyby na řádek.  
  
```  
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [NIB: Psát kód Ověřitelně bezpečného typu](https://msdn.microsoft.com/library/d18f10ef-3b48-4f47-8726-96714021547b)  
 [Bezpečnost typů a zabezpečení](https://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
