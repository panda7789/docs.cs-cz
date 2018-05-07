---
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: d61d710959f99dbc8a91441766a690eb7e9a365c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="4209---timeoutopeningsqlconnection"></a>4209 - TimeoutOpeningSqlConnection
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4209|  
|Klíčová slova|WFInstanceStore|  
|úroveň|Chyba|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že při pokusu o otevření připojení SQL došlo k vypršení časového limitu.  
  
## <a name="message"></a>Zpráva  
 Časový limit pokusu o otevření připojení SQL. Operace nebyla dokončena v přiděleném časovém limitu % 1. Čas přidělený tato operace mohla být část delší časový limit.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Časový limit|xs:String|Hodnota časového limitu pro otevření připojení SQL.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
