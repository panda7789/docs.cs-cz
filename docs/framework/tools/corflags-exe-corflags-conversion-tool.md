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
ms.openlocfilehash: 2ef10ba566842db26ed8c29643535c41aaca9806
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378663"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (CorFlags – převodní nástroj)
Nástroj CorFlags Conversion umožňuje konfigurovat CorFlags oddíl hlavičky bitové kopie přenosného spustitelného souboru.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|**/32BITPREF+**|Nastaví příznak 32BITPREFERRED. Aplikace běží jako 32bitový proces i na 64bitových platformách. Tento příznak je třeba nastavit pouze u souborů EXE. Pokud je příznak nastaven na knihovnu DLL, knihovnu DLL se nepodaří načíst v 64bitových procesů a <xref:System.BadImageFormatException> je vyvolána výjimka. Soubor EXE s tímto příznakem lze načíst do 64bitového procesu.<br /><br /> Nové v rozhraní .NET Framework 4.5.|  
|**/32BITPREF-**|Odstraní příznak 32BITPREFERRED.<br /><br /> Nové v rozhraní .NET Framework 4.5.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/ Force**|Vynutí aktualizaci i v případě sestavení se silným názvem. **Důležité:**  Při aktualizaci sestavení se silným názvem je nutné toto sestavení před spuštěním jeho kódu znovu podepsat.|  
|**/ Help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/ILONLY+**|Nastaví příznak ILONLY.|  
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
