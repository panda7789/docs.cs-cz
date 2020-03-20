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
ms.openlocfilehash: 9d5f8c80937c36e975d42d6efb0a83295cb28be9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73104985"
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (nástroj PEVerify)
Nástroj PEVerify pomáhá vývojářům generujícím Microsoft Intermediate Language (MSIL) (například autorům kompilátorů a vývojářům skriptovacích modulů) zjistit, zda jejich kód MSIL a přidružená metadata splňují požadavky na bezpečnost typů. Některé kompilátory generují kód ověřitelně bezpečného typu pouze tehdy, když se vyhnete určitým jazykovým konstrukcím. Pokud jako vývojář používáte takový kompilátor, můžete chtít ověřit, že nebyla ohrožena bezpečnost typů vašeho kódu. V této situaci můžete spustit nástroj PEVerify pro soubory ke kontrole jazyka MSIL a metadat.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*Název_souboru*|Přenosný spustitelný soubor (PE), pro který chcete zkontrolovat jazyk MSIL a metadata.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/break=** *maxErrorCount*|Přeruší ověřování po chybách *maxErrorCount.*<br /><br /> Tento parametr není podporován v rozhraní .NET Framework verze 2.0 a vyšší.|  
|**/hodiny**|Změří a oznámí následující časy ověření v milisekundách:<br /><br /> **MD Val. cyklus**<br /> Cyklus ověření metadat<br /><br /> **MD Val. čistý**<br /> Čisté ověření metadat<br /><br /> **IL Ver. cyklus**<br /> Cyklus ověřování Microsoft Intermediate Language (MSIL)<br /><br /> **IL Ver čistý**<br /> Čisté ověřování MSIL<br /><br /> **Cyklus MD Val.** a **otevírací doba IL Ver.** zahrnují čas potřebný k provedení nezbytných postupů spuštění a vypnutí. **MD Val. pure** a **IL Ver pure** times odrážejí čas potřebný k provedení pouze ověření nebo ověření.|  
|**/nápověda**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/hvýsledek**|Zobrazí kódy chyb v šestnáctkovém formátu.|  
|**/ignore=** *hex.code* [, *hex.code*]|Ignoruje zadané kódy chyb.|  
|**/ignore=@** *responseFile*|Ignoruje kódy chyb uvedené v zadaném souboru odpovědí.|  
|**/il**|Provádí kontroly ověření bezpečnosti typu MSIL pro metody implementované v sestavení určeném *názvem souboru*. Nástroj vrátí podrobné popisy pro každý nalezený problém, pokud nezadáte **/quiet** možnost.|  
|**/md**|Provádí kontroly ověření metadat u sestavení určeného *názvem souboru*. Prochází kompletní strukturu metadat v souboru a hlásí všechny zaznamenané problémy s ověřením.|  
|**/nologo**|Potlačí zobrazení informací o verzi a autorských právech produktu.|  
|**/nosymboly**|V rozhraní .NET Framework verze 2.0 potlačí zobrazování čísel řádků z důvodu zpětné kompatibility.|  
|**/tichý**|Nastaví tichý režim; potlačí výstup hlášení problémů ověření. Nástroj Peverify.exe stále hlásí, zda je soubor typově bezpečný, ale již nehlásí informace o problémech, které brání v ověření bezpečnosti typu.|  
|`/transparent`|Ověří pouze transparentní metody.|  
|**/jedinečný**|Ignoruje opakující se kódy chyb.|  
|**/podrobné informace**|V rozhraní .NET Framework verze 2.0 zobrazí další informace ve zprávách ověření MSIL.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Modul Common Language Runtime se opírá o typově bezpečné spuštění kódu aplikace k podpoře vynucení bezpečnostních a izolačních mechanismů. Za normálních okolností kód, který není [prokazatelně typ bezpečné](../../standard/security/key-security-concepts.md#type-safety-and-security) nelze spustit, i když můžete nastavit zásady zabezpečení povolit provádění důvěryhodného, ale neověřitelný kód.  
  
 Pokud nejsou zadány možnosti **/md** ani **/il,** program Peverify.exe provede oba typy kontrol. Peverify.exe nejprve provede **kontroly /md.** Pokud nejsou žádné chyby, **/il** kontroly jsou prováděny. Pokud zadáte **/md** a **/il**, **/il** kontroly jsou prováděny i v případě, že jsou chyby v metadatech. Pokud tedy nejsou k dispozici žádné chyby metadat, **peverify** *peverify název souboru* je ekvivalentní **peverify** *název souboru* **/md** **/il**.  
  
 Nástroj Peverify.exe provádí komplexní kontroly MSIL u platných metadat na základě analýzy datového toku a seznamu několika stovek pravidel. Podrobné informace o kontrolách, které nástroj Peverify.exe provádí, naleznete v části Specifikace ověření metadat a Specifikace sady instrukcí msil ve složce Tools Developers Guide v sadě Windows SDK.  
  
 Všimněte si, že rozhraní .NET Framework verze `byref` 2.0 nebo novější podporuje `dup` `ldsflda`ověřitelné `ldelema` `call` výnosy zadané pomocí následujících pokynů msil: , , `unbox` `ldflda`, a .  
  
## <a name="examples"></a>Příklady  
 Následující příkaz provádí kontroly ověření metadat a kontroly ověření bezpečnosti typu MSIL pro metody implementované v sestavení `myAssembly.exe`.  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 Po úspěšném dokončení výše uvedeného požadavku nástroj Peverify.exe zobrazí následující zprávu.  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 Následující příkaz provádí kontroly ověření metadat a kontroly ověření bezpečnosti typu MSIL pro metody implementované v sestavení `myAssembly.exe`. Nástroj zobrazí čas potřebný k provedení těchto kontrol.  
  
```console  
peverify myAssembly.exe /md /il /clock  
```  
  
 Po úspěšném dokončení výše uvedeného požadavku nástroj Peverify.exe zobrazí následující zprávu.  
  
```output
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 Následující příkaz provádí kontroly ověření metadat a kontroly ověření bezpečnosti typu MSIL pro metody implementované v sestavení `myAssembly.exe`. Nástroj Peverify.exe se však zastaví, jakmile dosáhne maximálního počtu 100 chyb. Tento nástroj rovněž ignoruje zadané kódy chyb.  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 Následující příkaz vytváří stejný výsledek jako předchozí příklad, ale určuje kódy chyb, `ignoreErrors.rsp`které chcete ignorovat v souboru odpovědí .  
  
```console  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 Soubor odpovědí může obsahovat seznam kódů chyb oddělených čárkami.  
  
```text
0x12345678, 0xABCD1234  
```  
  
 Soubor odpovědí lze také naformátovat s jedním kódem chyby na řádek.  
  
```text
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Psaní ověřitelně typově bezpečného kódu](../misc/code-access-security-basics.md#typesafe_code)
- [Bezpečnost a zabezpečení typů](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
