---
title: 'Základní komunikace: Přenosové kanály TCP'
ms.date: 03/30/2017
ms.assetid: d5cd057f-faec-4e21-ae0e-18bbc22bcfb1
ms.openlocfilehash: 0dfbf939b39d53f104d749e0c0d24e04a05185e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929919"
---
# <a name="core-communications-tcp-transport-channels"></a>Základní komunikace: Přenosové kanály TCP
Toto téma uvádí všechny výjimky generované přenosové kanály TCP.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód zdroje|Řetězec prostředku|  
|-------------------|---------------------|  
|SocketCloseReadTimeout|Vzdálený koncový bod soketu zadané nereagovala na požadavek zavření v rámci zadaného přiděleného časového limitu. Je možné, že vzdálený koncový bod nevolá zavření po přijetí signálu EOF (null) z operace příjmu. Čas přidělený této operaci pravděpodobně částí delšího časového limitu.|
