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
ms.openlocfilehash: e70324192f56214d273ae2a819a9c08be7d49b1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (nástroj PEVerify)
Nástroj PEVerify pomáhá vývojářům generujícím Microsoft Intermediate Language (MSIL) (například autorům kompilátorů a vývojářům skriptovacích modulů) zjistit, zda jejich kód MSIL a přidružená metadata splňují požadavky na bezpečnost typů. Některé kompilátory generují kód ověřitelně bezpečného typu pouze tehdy, když se vyhnete určitým jazykovým konstrukcím. Pokud jako vývojář používáte takový kompilátor, můžete chtít ověřit, že nebyla ohrožena bezpečnost typů vašeho kódu. V této situaci můžete spustit nástroj PEVerify pro soubory ke kontrole jazyka MSIL a metadat.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
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
|**/ Rozdělit =** *maxErrorCount*|Zruší ověření po *maxErrorCount* chyby.<br /><br /> Tento parametr není podporován v rozhraní .NET Framework verze 2.0 a vyšší.|  
|**/Clock**|Změří a oznámí následující časy ověření v milisekundách:<br /><br /> **MD úč.hod cyklu**<br /> Cyklus ověření metadat<br /><br /> **MD úč.hod čisté**<br /> Čisté ověření metadat<br /><br /> **Cyklus IL verze**<br /> Cyklus ověřování Microsoft Intermediate Language (MSIL)<br /><br /> **Čistého IL Ver**<br /> Čisté ověřování MSIL<br /><br /> **MD úč.hod cyklus** a **IL verze cyklus** časy zahrnout čas potřebný k provést nezbytné postupy spuštění a vypnutí. **MD úč.hod čistý** a **čistého IL Ver** časy reflektovat čas potřebné k provedení ověření nebo pouze ověření.|  
|**/ Help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/HRESULT**|Zobrazí kódy chyb v šestnáctkovém formátu.|  
|**/ Ignorovat =** *hex.code* [, *hex.code*]|Ignoruje zadané kódy chyb.|  
|**/ Ignorovat = @** *responseFile*|Ignoruje kódy chyb uvedené v zadaném souboru odpovědí.|  
|**/IL**|Provádí kontroly pro zabezpečení ověření MSIL typ pro metody implementované v sestavení určeného *filename*. Nástroj Vrátí podrobný popis pro jednotlivé problémy najít nezadáte **/quiet** možnost.|  
|**/md**|Provádí ověřovací kontroly metadata sestavení s určeného *filename*. Prochází kompletní strukturu metadat v souboru a hlásí všechny zaznamenané problémy s ověřením.|  
|**/nologo**|Potlačí zobrazení informací o verzi a autorských právech produktu.|  
|**/nosymbols**|V rozhraní .NET Framework verze 2.0 potlačí zobrazování čísel řádků z důvodu zpětné kompatibility.|  
|**/quiet**|Nastaví tichý režim; potlačí výstup hlášení problémů ověření. Nástroj Peverify.exe stále hlásí, zda je soubor typově bezpečný, ale již nehlásí informace o problémech, které brání v ověření bezpečnosti typu.|  
|`/transparent`|Ověří pouze transparentní metody.|  
|**/ Jedinečný**|Ignoruje opakující se kódy chyb.|  
|**/verbose**|V rozhraní .NET Framework verze 2.0 zobrazí další informace ve zprávách ověření MSIL.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Modul Common Language Runtime se opírá o typově bezpečné spuštění kódu aplikace k podpoře vynucení bezpečnostních a izolačních mechanismů. Za normálních okolností kód, který není [ověřitelný typ](http://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc) nelze spustit, i když můžete nastavit zásady zabezpečení pro povolení spuštění kódu důvěryhodné, ale nelze ověřit.  
  
 Pokud **/md** ani **/il** jsou zadány možnosti, Peverify.exe provede oba typy kontrol. Provede PEVerify.exe **/md** nejprve hledá. Pokud nejsou žádné chyby **/il** kontroly se provádějí. Pokud zadáte oba **/md** a **/il**, **/il** kontroly se provádějí i v případě, že jsou chyby v metadatech. Proto v případě, že nejsou žádné chyby metadat **peverify** *filename* je ekvivalentní **peverify** *filename* **/md** **/il**.  
  
 Nástroj Peverify.exe provádí komplexní kontroly MSIL u platných metadat na základě analýzy datového toku a seznamu několika stovek pravidel. Podrobné informace o kontrolách Peverify.exe provádí, najdete v části "Ověření specifikace metadat" a "MSIL instrukcí nastavit specifikace" ve složce Nástroje Příručka pro vývojáře v [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
 Rozhraní .NET Framework verze 2.0 nebo novější podporuje ověřitelný `byref` vrátí zadán pomocí následujících pokynů MSIL: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` a `unbox`.  
  
## <a name="examples"></a>Příklady  
 Tento příkaz provádí metadata ověřovací kontroly a kontroly pro zabezpečení ověření MSIL typ pro metody implementované v sestavení `myAssembly.exe`.  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 Po úspěšném dokončení výše uvedeného požadavku nástroj Peverify.exe zobrazí následující zprávu.  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 Tento příkaz provádí metadata ověřovací kontroly a kontroly pro zabezpečení ověření MSIL typ pro metody implementované v sestavení `myAssembly.exe`. Nástroj zobrazí čas potřebný k provedení těchto kontrol.  
  
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
  
 Tento příkaz provádí metadata ověřovací kontroly a kontroly pro zabezpečení ověření MSIL typ pro metody implementované v sestavení `myAssembly.exe`. Nástroj Peverify.exe se však zastaví, jakmile dosáhne maximálního počtu 100 chyb. Tento nástroj rovněž ignoruje zadané kódy chyb.  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 Následující příkaz vytvoří stejný výsledek jako výše předchozí příklad, ale Určuje kódy chyb ignorovat v souboru odpovědí, `ignoreErrors.rsp`.  
  
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
 [NIB: Zápis typ ověřitelný kód](http://msdn.microsoft.com/library/d18f10ef-3b48-4f47-8726-96714021547b)  
 [Typ zabezpečení a zabezpečení](http://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
