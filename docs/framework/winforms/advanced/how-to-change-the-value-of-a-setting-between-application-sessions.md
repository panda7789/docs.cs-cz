---
title: 'Postupy: Změna hodnoty nastavení mezi relacemi aplikace'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: c1626cea581e5c180665d0ce805dea3e67f27a05
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714356"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>Postupy: Změna hodnoty nastavení mezi relacemi aplikace
V některých případech můžete chtít změnit hodnoty nastavení mezi relacemi aplikace poté, co byl zkompilován a nasazení aplikace. Například můžete chtít změnit připojovací řetězec tak, aby odkazoval na správnou databázi umístění. Protože návrhových nástrojů nejsou k dispozici, poté, co byl zkompilován a nasazení aplikace, musíte změnit hodnotu nastavení v souboru ručně.  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a>Chcete-li změnit hodnoty nastavení mezi relacemi aplikace  
  
1.  Pomocí Microsoft Notepad nebo některé jiné text nebo editoru XML otevřete soubor .config přidruženého k aplikaci.  
  
2.  Vyhledejte položku pro nastavení, které chcete změnit. By měl vypadat podobně jako v příkladu níže uvedené.  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  Zadejte novou hodnotu pro nastavení a soubor uložte.  
  
## <a name="see-also"></a>Viz také:
- [Použití nastavení aplikace a uživatelských nastavení](using-application-settings-and-user-settings.md)
- [Přehled nastavení aplikace](application-settings-overview.md)
