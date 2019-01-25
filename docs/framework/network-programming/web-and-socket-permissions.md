---
title: Web a oprávnění soketu
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- positions [.NET Framework], accepting
- sockets, permissions
- network, permissions
- Internet, permissions
- Network Resources
- SocketPermission class, about SocketPermission class
- positions [.NET Framework], connecting
- WebPermission class, about WebPermission class
- permissions [.NET Framework], sockets
- security [.NET Framework], Internet
- positions [.NET Framework], granting
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
ms.openlocfilehash: b4395d26114425556f0457f03667d0f95f786ca7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677638"
---
# <a name="web-and-socket-permissions"></a>Web a oprávnění soketu
Internetové zabezpečení pro aplikace využívající <xref:System.Net> obor názvů poskytuje <xref:System.Net.WebPermission> a <xref:System.Net.SocketPermission> třídy. **Oprávnění WebPermission** třídy ovládací prvky aplikace přímo do data žádosti z identifikátoru URI nebo identifikátor URI neslouží k Internetu. **SocketPermission** třídy aplikaci prvku správné použití ovládacích prvků <xref:System.Net.Sockets.Socket> tak, aby přijímal data na jiný místní port nebo se obrátit na vzdálené zařízení pomocí protokolu přenosu na jiné adrese založené na hostiteli, číslo portu, a Přenosový protokol soketu.  
  
 Která oprávnění třída použijete, závisí na váš typ aplikace. Aplikace, které používají <xref:System.Net.WebRequest> a jejích potomků, používejte **oprávnění WebPermission** třídy pro správu oprávnění. Používejte aplikace, které používají přístup na úrovni soketu **SocketPermission** třídy pro správu oprávnění.  
  
 **Oprávnění WebPermission** a **SocketPermission** definovat dvě oprávnění: přijmout a připojit. Přijměte uděluje právo k zodpovězení příchozí připojení z jiného aplikace. Připojte se uděluje právo k navázání připojení k jiné strany aplikace.  
  
 Pro **SocketPermission** instancí, přijměte znamená, že aplikace může přijmout příchozí spojení na místní adresu přenosu; připojení znamená, že aplikace může připojit k adrese některé přenos vzdálený (nebo místní).  
  
 Pro **oprávnění WebPermission** instancí, přijměte znamená, že aplikace můžete exportovat identifikátor URI, řídí **oprávnění WebPermission** ve světě; připojení znamená, že aplikace může použít tento identifikátor URI (ať už jde vzdálené nebo místní).  
  
## <a name="see-also"></a>Viz také:
- [Zabezpečení](../../../docs/standard/security/index.md)
- [Zabezpečení v síťovém programování](../../../docs/framework/network-programming/security-in-network-programming.md)
