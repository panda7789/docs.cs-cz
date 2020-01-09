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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715716"
---
# <a name="storeadmexe-isolated-storage-tool"></a>Storeadm.exe (nástroj izolovaného úložiště)
Nástroj izolované úložiště vypíše seznam všech existujících úložišť pro aktuálního uživatele nebo všechna existující úložiště odebere.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/h**[**elp**]|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/list**|Zobrazí všechna existující úložiště pro aktuálního uživatele. Jedná se o úložiště pro všechny aplikace nebo sestavení spuštěná tímto uživatelem.|  
|**/Machine**|Vybere úložiště počítače. Tuto možnost použijte spolu s možností **/list** nebo **/Remove** a určete tak, že se akce má vztahovat na úložiště počítače.<br /><br /> Novinky v rozhraní .NET Framework 2.0|  
|**/quiet**|Nastaví tichý režim; potlačí informační výstup tak, aby se zobrazovaly pouze chybové zprávy.|  
|**/Remove**|Permanentně odstraní všechna existující úložiště pro aktuálního uživatele.|  
|**/roaming**|Vybere roamingové úložiště. Tuto možnost použijte spolu s možnostmi **/list** nebo **/Remove** k určení, že by akce měla platit pro roamingové úložiště.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Jestliže spustíte nástroj Storeadm.exe z příkazového řádku bez zadání jakýchkoli možností, zobrazí se syntaxe a možnosti pro tento nástroj.  
  
 Možnosti **/list** a **/Remove** jsou obvykle používány po jednom. Pokud jsou však zadány dvě nebo více možností, budou provedeny v pořadí, ve kterém se zobrazí na příkazovém řádku.  
  
 Aplikace mají možnost ukládat do jednoho nebo dvou úložišť pro uživatele nebo do úložiště počítače:  
  
- Místní úložiště existuje v umístění, ve kterém se garantuje roaming (ve Windows 2000 a novějším), a to i v případě, že je pro uživatele povolen roaming dat uživatele.  
  
- Roamingové úložiště existuje v umístění, které se může přenášet, ale může to udělat jenom v případě, že je pro uživatele povolený roaming prostřednictvím správy systému Windows NT.  
  
- Úložiště počítače je společné pro všechny uživatele počítače a je uloženo ve společném adresáři v daném počítači.  
  
    > [!NOTE]
    > Úložiště počítače je v rozhraní .NET Framework verze 2.0 novinkou.  
  
 To, zda je roaming skutečně povolen pro určitého uživatele, nemá vliv na správu nástroje Storeadm.exe. Při spuštění nástroje bez jakýchkoli možností se použijí všechny akce na místní úložiště. Spuštění nástroje s možností **/roaming** aplikuje všechny akce do úložiště, které je možné přenášet na roaming. Spuštění nástroje s možností **/Machine** použije všechny akce na úložiště počítače.  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](index.md)
- [Izolované úložiště](../../standard/io/isolated-storage.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
