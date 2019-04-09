---
title: Clrver.exe (nástroj verze CLR)
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28ac90eadcc7a13fe946aabf17973ebc602c9d4a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084593"
---
# <a name="clrverexe-clr-version-tool"></a>Clrver.exe (nástroj verze CLR)
Nástroj CLR Version (Clrver.exe) vypíše všechny verze modulu Common Language Runtime (CLR) nainstalované v počítači.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
clrver [option]  
```  
  
## <a name="options"></a>Možnosti  
  
|Možnost|Popis|  
|------------|-----------------|  
|`-all`|Zobrazí všechny procesy v počítači využívající modul CLR.|  
|*Identifikátor PID*|Zobrazí verze modulu CLR využívané procesem se zadaným identifikátorem ID procesu (PID).|  
|`-?`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Při volání nástroje Clrver.exe bez použití možností se zobrazí všechny nainstalované verze modulu CLR. Pokud zadáte identifikátor PID pro jiného uživatele, musíte mít oprávnění správce, chcete-li získat informace o verzi.  
  
> [!NOTE]
>  Nástroj Řízení uživatelských účtů (UAC) v systému Windows Vista a novějším určuje oprávnění uživatele. Pokud jste členem předdefinované skupiny Administrators, máte přiřazeny dva přístupové tokeny run-time: token přístupu uživatele se standardním oprávněním a token přístupu správce. Ve výchozím nastavení máte roli standardního uživatele. Chcete-li spustit kód vyžadující oprávnění správce, musíte nejprve zvýšit své oprávnění ze standardního uživatele na správce. Můžete tak učinit při spouštění příkazového řádku kliknutím pravým tlačítkem myši na ikonu příkazového řádku a označením, že chcete nástroj spustit jako správce.  
  
 Při pokusu o určení verze modulu CLR pro procesy SYSTEM, LOCAL SERVICE a NETWORK SERVICE dojde k zobrazení zprávy, že PID neexistuje.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz zobrazí všechny verze modulu CLR nainstalované v počítači.  
  
 `clrver`  
  
 Následující příkaz zobrazí verzi modulu CLR používanou procesem 128.  
  
 `clrver 128`  
  
 Následující příkaz zobrazí všechny spravované procesy a verzi modulu CLR, kterou používají.  
  
 `Clrver -all`  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
