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
ms.openlocfilehash: 21b9881f1275c6a9343421131af478e11b826073
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222724"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (CorFlags – převodní nástroj)
Nástroj CorFlags Conversion umožňuje konfigurovat CorFlags oddíl hlavičky bitové kopie přenosného spustitelného souboru.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
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
|**/ 32 BITŮ [NO] +**|Nastaví příznak 32BITREQUIRED.|  
|**/ 32 BITŮ [NO]-**|Odstraní příznak 32BITREQUIRED.|  
|**/32BITPREF+**|Nastaví příznak 32BITPREFERRED. Aplikace běží jako 32bitový proces i na 64bitových platformách. Tento příznak je třeba nastavit pouze u souborů EXE. Pokud je příznak nastaven na knihovnu DLL, knihovnu DLL se nepodaří načíst v 64bitových procesů a <xref:System.BadImageFormatException> je vyvolána výjimka. Soubor EXE s tímto příznakem lze načíst do 64bitového procesu.<br /><br /> Novinkou [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|  
|**/32BITPREF-**|Odstraní příznak 32BITPREFERRED.<br /><br /> Novinkou [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/ Force**|Vynutí aktualizaci i v případě sestavení se silným názvem. **Důležité:**  Při aktualizaci sestavení se silným názvem je nutné toto sestavení před spuštěním jeho kódu znovu podepsat.|  
|**/ Help**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/ILONLY+**|Nastaví příznak ILONLY.|  
|**/ILONLY-**|Odstraní příznak ILONLY.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/ RevertCLRHeader**|Vrátí verzi hlavičky CLR na 2.0.|  
|**/ UpgradeCLRHeader**|Aktualizuje verzi hlavičky CLR na 2.5. **Poznámka:**  Pro nativní spuštění musí mít sestavení hlavičku modulu CLR verze 2.5 nebo vyšší.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud nejsou zadány žádné parametry, zobrazí nástroj CorFlags Conversion příznaky pro zadané sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [64bitové aplikace](../../../docs/framework/64-bit-apps.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
