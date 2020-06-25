---
title: Peverify.exe (nástroj PEVerify)
description: Pomocí Peverify.exe (přenosné spustitelné soubory) můžete určit, jestli kód jazyka MSIL (Microsoft Intermediate Language) & metadata splňují standardy zabezpečení typu v .NET.
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
ms.openlocfilehash: 478c04a45c7f9d3ad568a6bc4a12a89fe786583a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325620"
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (nástroj PEVerify)

Nástroj Nástroj PEVerify pomáhá vývojářům vygenerovat jazyk MSIL (Microsoft Intermediate Language) (například moduly pro zápisy kompilátoru a vývojáře skriptovacího stroje), aby určil, zda jejich kód jazyka MSIL a přidružená metadata splňují požadavky na bezpečnost typů. Některé kompilátory generují kód ověřitelně bezpečného typu pouze tehdy, když se vyhnete určitým jazykovým konstrukcím. Pokud používáte takový kompilátor, můžete chtít ověřit, že jste neohrozili bezpečnost typů kódu. Můžete spustit nástroj Nástroj PEVerify v souborech a ověřit jazyk MSIL a metadata.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).
  
## <a name="syntax"></a>Syntaxe  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*Bitmap*|Přenosný spustitelný soubor (PE), pro který chcete zkontrolovat jazyk MSIL a metadata.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Break =** *maxErrorCount*|Po *maxErrorCount* chybách zruší ověření.<br /><br /> Tento parametr není podporován v rozhraní .NET Framework verze 2.0 a vyšší.|  
|**/clock**|Změří a oznámí následující časy ověření v milisekundách:<br /><br /> **MD Val. koloběh**<br /> Cyklus ověření metadat<br /><br /> **MD Val. Pure**<br /> Čisté ověření metadat<br /><br /> **IL – ver. koloběh**<br /> Cyklus ověřování Microsoft Intermediate Language (MSIL)<br /><br /> **IL – ver – čistá**<br /> Čisté ověřování MSIL<br /><br /> Časy **MD Val. Cycle** a **Il ver. Cycle** zahrnují dobu potřebnou k provedení nezbytných postupů spuštění a vypnutí. Časy **MD Val. Pure** a **Il verze Pure** odrážejí dobu potřebnou k provedení ověřování nebo ověření.|  
|**/Help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/hresult**|Zobrazí kódy chyb v šestnáctkovém formátu.|  
|**/Ignore =** *Hex. Code* [, *Hex. Code*]|Ignoruje zadané kódy chyb.|  
|**/Ignore = @** *responseFile*|Ignoruje kódy chyb uvedené v zadaném souboru odpovědí.|  
|**/Il**|Provede kontroly ověřování bezpečnosti typů jazyka MSIL pro metody implementované v sestavení určeném parametrem *filename*. Nástroj vrátí podrobné popisy jednotlivých nalezených problémů, pokud nezadáte možnost **/quiet** .|  
|**/MD**|Provádí kontroly ověřování metadat u sestavení určeného parametrem *filename*. Tato možnost provede úplnou strukturu metadat v rámci souboru a oznámí všechny zjištěné problémy s ověřením.|  
|**/nologo**|Potlačí zobrazení informací o verzi a autorských právech produktu.|  
|**/nosymbols**|V rozhraní .NET Framework verze 2.0 potlačí zobrazování čísel řádků z důvodu zpětné kompatibility.|  
|**parametr**|Nastaví tichý režim; potlačí výstup hlášení problémů ověření. Nástroj Peverify.exe stále hlásí, zda je soubor typově bezpečný, ale již nehlásí informace o problémech, které brání v ověření bezpečnosti typu.|  
|`/transparent`|Ověří pouze transparentní metody.|  
|**/Unique**|Ignoruje opakující se kódy chyb.|  
|**/verbose**|V rozhraní .NET Framework verze 2.0 zobrazí další informace ve zprávách ověření MSIL.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Modul Common Language Runtime se opírá o typově bezpečné spuštění kódu aplikace k podpoře vynucení bezpečnostních a izolačních mechanismů. Kód, který není [ověřovatelně typově bezpečný](../../standard/security/key-security-concepts.md#type-safety-and-security) , se normálně nedá spustit, i když můžete nastavit zásady zabezpečení, které umožňují spuštění důvěryhodného, ale neověřitelného kódu.  
  
 Pokud nejsou zadány žádné možnosti **/MD** ani **/Il** , Peverify.exe provádí oba typy kontrol. Peverify.exe nejprve provádí kontroly **/MD** . V případě, že nejsou k dispozici žádné chyby, provedou se kontroly **/Il** . Pokud zadáte obě **/MD** i **/Il**, kontroly **/Il** se provedou, i když v metadatech dojde k chybám. Proto pokud nejsou k dispozici žádné chyby metadat, *název souboru* **Nástroj PEVerify** je ekvivalentní **Nástroj PEVerify** *název_souboru* **/MD** **/Il**.  
  
 Nástroj Peverify.exe provádí komplexní kontroly MSIL u platných metadat na základě analýzy datového toku a seznamu několika stovek pravidel. Podrobné informace o kontrolách, které Peverify.exe provádí, naleznete v části specifikace ověření metadat a specifikace sady MSIL instrukcí ve složce průvodce pro vývojáře v Windows SDK.  
  
.NET Framework verze 2,0 nebo novější podporuje ověřitelné `byref` návraty zadané pomocí následujících instrukcí jazyka MSIL: `dup` , `ldsflda` , `ldflda` ,, a `ldelema` `call` `unbox` .  
  
## <a name="examples"></a>Příklady  
 Následující příkaz provede kontroly ověřování metadat a ověření bezpečnosti typů jazyka MSIL pro metody implementované v sestavení `myAssembly.exe` .  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 Po úspěšném dokončení výše uvedeného požadavku nástroj Peverify.exe zobrazí následující zprávu.  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 Následující příkaz provede kontroly ověřování metadat a ověření bezpečnosti typů jazyka MSIL pro metody implementované v sestavení `myAssembly.exe` . Nástroj zobrazí čas potřebný k provedení těchto kontrol.  
  
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
  
 Následující příkaz provede kontroly ověřování metadat a ověření bezpečnosti typů jazyka MSIL pro metody implementované v sestavení `myAssembly.exe` . Nástroj Peverify.exe se však zastaví, jakmile dosáhne maximálního počtu 100 chyb. Tento nástroj rovněž ignoruje zadané kódy chyb.  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 Následující příkaz vytvoří stejný výsledek jako výše předchozí příklad, ale Určuje kódy chyb, které se mají v souboru odpovědí ignorovat `ignoreErrors.rsp` .  
  
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
- [Zápis ověřitelného kódu bezpečného typu](../misc/code-access-security-basics.md#typesafe_code)
- [Bezpečnost typů a zabezpečení](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [Výzvy příkazového řádku](developer-command-prompt-for-vs.md)
