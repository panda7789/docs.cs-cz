---
title: CorFlags.exe (CorFlags – převodní nástroj)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: e1251b6660db45f3af4f6e57114b1b10da18bd0a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129866"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (CorFlags – převodní nástroj)
Nástroj CorFlags Conversion umožňuje konfigurovat CorFlags oddíl hlavičky bitové kopie přenosného spustitelného souboru.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).  
  
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
|:------------|-----------------|  
|`-32BIT[REQ]+`|Nastaví příznak 32BITREQUIRED.|  
|`-32BIT[REQ]-`|Odstraní příznak 32BITREQUIRED.|  
|`-32BITPREF+`|Nastaví příznak 32BITPREFERRED. Aplikace běží jako 32bitový proces i na 64bitových platformách. Tento příznak je třeba nastavit pouze u souborů EXE. Pokud je příznak nastaven na dll, DLL se nezdaří načíst <xref:System.BadImageFormatException> v 64bitové procesy a je vyvolána výjimka. Soubor EXE s tímto příznakem lze načíst do 64bitového procesu.<br /><br /> Novinka v rozhraní .NET Framework 4.5.|  
|`-32BITPREF-`|Odstraní příznak 32BITPREFERRED.<br /><br /> Novinka v rozhraní .NET Framework 4.5.|  
|`-?`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|`-Force`|Vynutí aktualizaci i v případě sestavení se silným názvem. **Důležité:**  Pokud aktualizujete sestavení se silným názvem, musíte jej znovu podepsat před spuštěním jeho kódu.|  
|`-help`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|`-ILONLY+`|Nastaví příznak ILONLY.|  
|`-ILONLY-`|Odstraní příznak ILONLY.|  
|`-nologo`|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|`-RevertCLRHeader`|Vrátí verzi hlavičky CLR na 2.0.|  
|`-UpgradeCLRHeader`|Aktualizuje verzi hlavičky CLR na 2.5. **Poznámka:**  Sestavení musí mít clr záhlaví verze 2.5 nebo vyšší spustit nativně.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud nejsou zadány žádné parametry, zobrazí nástroj CorFlags Conversion příznaky pro zadané sestavení.  
  
## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [64bitové aplikace](../64-bit-apps.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
