---
title: Storeadm.exe (nástroj izolovaného úložiště)
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 29dd8ae38e2635f92c5be2b4d856f03a2e3e5767
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221515"
---
# <a name="storeadmexe-isolated-storage-tool"></a>Storeadm.exe (nástroj izolovaného úložiště)
Nástroj izolované úložiště vypíše seznam všech existujících úložišť pro aktuálního uživatele nebo všechna existující úložiště odebere.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/h**[**elp**]|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/ list**|Zobrazí všechna existující úložiště pro aktuálního uživatele. Jedná se o úložiště pro všechny aplikace nebo sestavení spuštěná tímto uživatelem.|  
|**/ Machine**|Vybere úložiště počítače. Tuto možnost použijte spolu s **/list** nebo **/remove** možnost určit, že akce se má použít na úložiště počítače.<br /><br /> Novinky v rozhraní .NET Framework 2.0|  
|**/quiet**|Nastaví tichý režim; potlačí informační výstup tak, aby se zobrazovaly pouze chybové zprávy.|  
|**/ Remove**|Permanentně odstraní všechna existující úložiště pro aktuálního uživatele.|  
|**/ roaming**|Vybere roamingové úložiště. Tuto možnost použijte spolu s **/list** nebo **/remove** možností, které určují, akce se má použít na roamingové úložiště.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Jestliže spustíte nástroj Storeadm.exe z příkazového řádku bez zadání jakýchkoli možností, zobrazí se syntaxe a možnosti pro tento nástroj.  
  
 **/List** a **/remove** možnosti jsou běžně používané jeden po druhém, ale pokud nejsou zadány dva nebo více možností, budou provedeny v pořadí, v jakém jsou uvedeny v příkazovém řádku.  
  
 Aplikace mají možnost ukládat do jednoho nebo dvou úložišť pro uživatele nebo do úložiště počítače:  
  
-   Místní úložiště existuje v umístění, ke kterému je zaručeno, že roaming (ve Windows 2000 a novějších verzích) i v případě, že uživatel datový roaming je povolená pro uživatele.  
  
-   Roamingové úložiště existuje v umístění, které lze přesouvat, ale můžete tak učinit pouze pokud je roaming povolen pro daného uživatele prostřednictvím správy systému Windows NT.  
  
-   Úložiště počítače je společné pro všechny uživatele počítače a je uloženo ve společném adresáři v daném počítači.  
  
    > [!NOTE]
    >  Úložiště počítače je v rozhraní .NET Framework verze 2.0 novinkou.  
  
 To, zda je roaming skutečně povolen pro určitého uživatele, nemá vliv na správu nástroje Storeadm.exe. Při spuštění nástroje bez jakýchkoli možností se použijí všechny akce na místní úložiště. Spuštění nástroje s **/ roaming** možnost použijí všechny akce na úložiště, které lze přesouvat. Spuštění nástroje s **/machine** možnost použijí všechny akce na úložiště počítače.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
