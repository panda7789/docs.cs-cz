---
title: 4209 – TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: d61d710959f99dbc8a91441766a690eb7e9a365c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774267"
---
# <a name="4209---timeoutopeningsqlconnection"></a>4209 – TimeoutOpeningSqlConnection
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4209|  
|klíčová slova|WFInstanceStore|  
|úroveň|Chyba|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že při pokusu o otevření připojení SQL došlo k vypršení časového limitu.  
  
## <a name="message"></a>Zpráva  
 Časový limit pokusu o otevření připojení SQL. Operace nebyla dokončena ve vyhrazeném časovém intervalu %1. Čas přidělený této operaci pravděpodobně částí delšího časového limitu.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|časový limit|xs:string|Hodnota časového limitu pro otevření připojení SQL.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
