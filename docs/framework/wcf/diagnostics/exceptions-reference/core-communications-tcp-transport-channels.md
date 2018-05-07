---
title: 'Základní komunikace: TCP přenosové kanály'
ms.date: 03/30/2017
ms.assetid: d5cd057f-faec-4e21-ae0e-18bbc22bcfb1
ms.openlocfilehash: 0dfbf939b39d53f104d749e0c0d24e04a05185e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="core-communications-tcp-transport-channels"></a>Základní komunikace: TCP přenosové kanály
Toto téma uvádí všechny výjimky generované přenosové kanály TCP.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|SocketCloseReadTimeout|Vzdálený koncový bod zadaný soketu nereagovala na žádost o uzavření v rámci zadaného přiděleném časovém limitu. Je možné, že vzdálený koncový bod není volání zavřít po přijetí signálu EOF (null) z operace příjmu. Čas přidělený tato operace mohla být část delší časový limit.|
