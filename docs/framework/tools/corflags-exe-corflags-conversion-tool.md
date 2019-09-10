---
title: CorFlags.exe (CorFlags – převodní nástroj)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4228da6efe22091c86de95d846c14f504d51457f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851287"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (CorFlags – převodní nástroj)
Nástroj CorFlags Conversion umožňuje konfigurovat CorFlags oddíl hlavičky bitové kopie přenosného spustitelného souboru.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Povinný parametr|Popis|  
|------------------------|-----------------|  
|`assembly`|Název sestavení, pro které chcete konfigurovat CorFlags.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/32BIT[REQ]+**|Nastaví příznak 32BITREQUIRED.|  
|**/32BIT[REQ]-**|Odstraní příznak 32BITREQUIRED.|  
|**/32BITPREF+**|Nastaví příznak 32BITPREFERRED. Aplikace běží jako 32bitový proces i na 64bitových platformách. Tento příznak je třeba nastavit pouze u souborů EXE. Pokud je příznak nastaven na knihovnu DLL, knihovna DLL se nenačte v 64ch procesech a <xref:System.BadImageFormatException> vyvolá se výjimka. Soubor EXE s tímto příznakem lze načíst do 64bitového procesu.<br /><br /> Novinka v .NET Framework 4,5.|  
|**/32BITPREF-**|Odstraní příznak 32BITPREFERRED.<br /><br /> Novinka v .NET Framework 4,5.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/Force.**|Vynutí aktualizaci i v případě sestavení se silným názvem. **Důležité:**  Při aktualizaci sestavení se silným názvem je nutné toto sestavení před spuštěním jeho kódu znovu podepsat.|  
|**/ Help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/ILONLY +**|Nastaví příznak ILONLY.|  
|**/ILONLY-**|Odstraní příznak ILONLY.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/RevertCLRHeader**|Vrátí verzi hlavičky CLR na 2.0.|  
|**/UpgradeCLRHeader**|Aktualizuje verzi hlavičky CLR na 2.5. **Poznámka:**  Pro nativní spuštění musí mít sestavení hlavičku modulu CLR verze 2.5 nebo vyšší.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud nejsou zadány žádné parametry, zobrazí nástroj CorFlags Conversion příznaky pro zadané sestavení.  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [64bitové aplikace](../../../docs/framework/64-bit-apps.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
