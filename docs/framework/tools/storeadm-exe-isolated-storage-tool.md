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
ms.openlocfilehash: 46e846eaf92835fb2a9130b85ed20749934ca5a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715716"
---
# <a name="storeadmexe-isolated-storage-tool"></a>Storeadm.exe (nástroj izolovaného úložiště)
Nástroj izolované úložiště vypíše seznam všech existujících úložišť pro aktuálního uživatele nebo všechna existující úložiště odebere.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/h**[**elp**]|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/seznam**|Zobrazí všechna existující úložiště pro aktuálního uživatele. Jedná se o úložiště pro všechny aplikace nebo sestavení spuštěná tímto uživatelem.|  
|**/stroj**|Vybere úložiště počítače. Tuto možnost použijte s parametrem **/list** nebo **/remove** a určete, že akce by se měla vztahovat na úložiště počítače.<br /><br /> Novinky v rozhraní .NET Framework 2.0|  
|**/tichý**|Nastaví tichý režim; potlačí informační výstup tak, aby se zobrazovaly pouze chybové zprávy.|  
|**/odebrat**|Permanentně odstraní všechna existující úložiště pro aktuálního uživatele.|  
|**/roaming**|Vybere roamingové úložiště. Tuto možnost použijte s možnostmi **/list** nebo **/remove** a určete, že akce by se měla vztahovat na cestovní úložiště.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Jestliže spustíte nástroj Storeadm.exe z příkazového řádku bez zadání jakýchkoli možností, zobrazí se syntaxe a možnosti pro tento nástroj.  
  
 Možnosti **/list** a **/remove** se obvykle používají jeden po druhém; pokud jsou však zadány dvě nebo více možností, budou provedeny v pořadí, ve kterém se zobrazí na příkazovém řádku.  
  
 Aplikace mají možnost ukládat do jednoho nebo dvou úložišť pro uživatele nebo do úložiště počítače:  
  
- Místní úložiště existuje v umístění, které je zaručeno, že nebude roaming (v systému Windows 2000 a novější) i v případě, že je pro uživatele povolen datový roaming uživatele.  
  
- Úložiště roamingu existuje v umístění, které se může přemísťovat, ale může tak učinit pouze v případě, že je pro uživatele povolen roaming prostřednictvím správy systému Windows NT.  
  
- Úložiště počítače je společné pro všechny uživatele počítače a je uloženo ve společném adresáři v daném počítači.  
  
    > [!NOTE]
    > Úložiště počítače je v rozhraní .NET Framework verze 2.0 novinkou.  
  
 To, zda je roaming skutečně povolen pro určitého uživatele, nemá vliv na správu nástroje Storeadm.exe. Při spuštění nástroje bez jakýchkoli možností se použijí všechny akce na místní úložiště. Spuštění nástroje s parametrem **/roaming** použije všechny akce pro úložiště, které je možné přejít. Spuštění nástroje s parametrem **/machine** použije všechny akce pro úložiště počítače.  
  
## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Izolované úložiště](../../standard/io/isolated-storage.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
