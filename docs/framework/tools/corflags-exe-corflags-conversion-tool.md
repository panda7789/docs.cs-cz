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
ms.openlocfilehash: d4a5b6d490387f2da441ad95bdf369f700cf2e9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400026"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (CorFlags – převodní nástroj)
Nástroj CorFlags Conversion umožňuje konfigurovat CorFlags oddíl hlavičky bitové kopie přenosného spustitelného souboru.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CorFlags.exe assembly [options]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Povinný parametr|Popis|  
|------------------------|-----------------|  
|`assembly`|Název sestavení, pro které chcete konfigurovat CorFlags.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/ 32BITOVÉ [NO] +**|Nastaví příznak 32BITREQUIRED.|  
|**/ 32BITOVÉ [NO]-**|Odstraní příznak 32BITREQUIRED.|  
|**/32BITPREF+**|Nastaví příznak 32BITPREFERRED. Aplikace běží jako 32bitový proces i na 64bitových platformách. Tento příznak je třeba nastavit pouze u souborů EXE. Pokud je nastavený příznak na knihovnu DLL, knihovny DLL nepodaří načíst v 64bitové procesy a <xref:System.BadImageFormatException> je vyvolána výjimka. Soubor EXE s tímto příznakem lze načíst do 64bitového procesu.<br /><br /> Novinka v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|  
|**/32BITPREF-**|Odstraní příznak 32BITPREFERRED.<br /><br /> Novinka v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/ Force**|Vynutí aktualizaci i v případě sestavení se silným názvem. **Důležité:** Pokud aktualizujete sestavení se silným názvem, musíte se odhlásit ho znovu před provedením jeho kód.|  
|**/ Help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/ILONLY+**|Nastaví příznak ILONLY.|  
|**/ILONLY-**|Odstraní příznak ILONLY.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/ RevertCLRHeader**|Vrátí verzi hlavičky CLR na 2.0.|  
|**/ UpgradeCLRHeader**|Aktualizuje verzi hlavičky CLR na 2.5. **Poznámka:** sestavení musí mít hlavička CLR verzi 2.5 nebo novější, abyste mohli spustit nativně.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud nejsou zadány žádné parametry, zobrazí nástroj CorFlags Conversion příznaky pro zadané sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [64bitové aplikace](../../../docs/framework/64-bit-apps.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
