---
title: "Storeadm.exe (nástroj izolovaného úložiště)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8351219b8352af7de534ebc5bd6521d5cf4773e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="storeadmexe-isolated-storage-tool"></a>Storeadm.exe (nástroj izolovaného úložiště)
Nástroj izolované úložiště vypíše seznam všech existujících úložišť pro aktuálního uživatele nebo všechna existující úložiště odebere.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/h**[**nápovědu**]|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/ list**|Zobrazí všechna existující úložiště pro aktuálního uživatele. Jedná se o úložiště pro všechny aplikace nebo sestavení spuštěná tímto uživatelem.|  
|**/ počítače**|Vybere úložiště počítače. Pomocí této možnosti se **/list** nebo **/odebrat** můžete určit, že akce by se měly používat k úložišti počítače.<br /><br /> Novinky v rozhraní .NET Framework 2.0|  
|**/quiet**|Nastaví tichý režim; potlačí informační výstup tak, aby se zobrazovaly pouze chybové zprávy.|  
|**/ Remove**|Permanentně odstraní všechna existující úložiště pro aktuálního uživatele.|  
|**/ roamingu**|Vybere roamingové úložiště. Pomocí této možnosti se **/list** nebo **/odebrat** možností, které určují, že akce by se měly používat k úložišti roamingu.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Jestliže spustíte nástroj Storeadm.exe z příkazového řádku bez zadání jakýchkoli možností, zobrazí se syntaxe a možnosti pro tento nástroj.  
  
 **/List** a **/odebrat** možnosti jsou obvykle používanými jeden po druhém, ale pokud jsou zadány dvě nebo více možností se bude provedena v pořadí, ve kterém jsou zobrazeny na příkazovém řádku.  
  
 Aplikace mají možnost ukládat do jednoho nebo dvou úložišť pro uživatele nebo do úložiště počítače:  
  
-   V umístění, které záruku, že není se bude používat roaming (v systému Windows 2000 a novější), i když je uživatel datový roaming je povolená pro uživatele existuje místní úložiště.  
  
-   Cestovní úložiště existuje v umístění, které je možné přesouvat, ale můžete tak učinit pouze pokud je roaming povolený pro uživatele na základě správy systému Windows NT.  
  
-   Úložiště počítače je společné pro všechny uživatele počítače a je uloženo ve společném adresáři v daném počítači.  
  
    > [!NOTE]
    >  Úložiště počítače je v rozhraní .NET Framework verze 2.0 novinkou.  
  
 To, zda je roaming skutečně povolen pro určitého uživatele, nemá vliv na správu nástroje Storeadm.exe. Při spuštění nástroje bez jakýchkoli možností se použijí všechny akce na místní úložiště. Spuštění nástroje s **/ roamingu** možnost se vztahuje k úložišti, který se bude moct přesouvat všechny akce. Spuštění nástroje s **/machine** možnost všechny akce se vztahuje na úložišti počítače.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
