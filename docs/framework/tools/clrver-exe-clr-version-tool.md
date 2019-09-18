---
title: Clrver.exe (nástroj verze CLR)
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a94965c106b6ec231e3f80802f82c76dfd5eac6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044759"
---
# <a name="clrverexe-clr-version-tool"></a>Clrver.exe (nástroj verze CLR)
Nástroj CLR Version (Clrver.exe) vypíše všechny verze modulu Common Language Runtime (CLR) nainstalované v počítači.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
clrver [option]  
```  
  
## <a name="options"></a>Možnosti  
  
|Možnost|Popis|  
|------------|-----------------|  
|`-all`|Zobrazí všechny procesy v počítači využívající modul CLR.|  
|*pid*|Zobrazí verze modulu CLR využívané procesem se zadaným identifikátorem ID procesu (PID).|  
|`-?`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Při volání nástroje Clrver.exe bez použití možností se zobrazí všechny nainstalované verze modulu CLR. Pokud zadáte identifikátor PID pro jiného uživatele, musíte mít oprávnění správce, chcete-li získat informace o verzi.  
  
> [!NOTE]
> Nástroj Řízení uživatelských účtů (UAC) v systému Windows Vista a novějším určuje oprávnění uživatele. Pokud jste členem předdefinované skupiny Administrators, máte přiřazeny dva přístupové tokeny run-time: token přístupu uživatele se standardním oprávněním a token přístupu správce. Ve výchozím nastavení máte roli standardního uživatele. Chcete-li spustit kód vyžadující oprávnění správce, musíte nejprve zvýšit své oprávnění ze standardního uživatele na správce. Můžete tak učinit při spouštění příkazového řádku kliknutím pravým tlačítkem myši na ikonu příkazového řádku a označením, že chcete nástroj spustit jako správce.  
  
 Při pokusu o určení verze modulu CLR pro procesy SYSTEM, LOCAL SERVICE a NETWORK SERVICE dojde k zobrazení zprávy, že PID neexistuje.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz zobrazí všechny verze modulu CLR nainstalované v počítači.  
  
 `clrver`  
  
 Následující příkaz zobrazí verzi modulu CLR používanou procesem 128.  
  
 `clrver 128`  
  
 Následující příkaz zobrazí všechny spravované procesy a verzi modulu CLR, kterou používají.  
  
 `Clrver -all`  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](index.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
