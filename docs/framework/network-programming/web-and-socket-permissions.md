---
title: "Webové a soketu oprávnění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 102d7d92384d77b5fbb56cd8c3eb859ec64bcca0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="web-and-socket-permissions"></a>Webové a soketu oprávnění
Zabezpečení Internetu pro aplikace pomocí <xref:System.Net> obor názvů poskytuje <xref:System.Net.WebPermission> a <xref:System.Net.SocketPermission> třídy. **Oprávnění WebPermission** třída ovládací prvky aplikace k data žádosti z identifikátoru URI nebo identifikátor URI sloužit k Internetu. **SocketPermission** třídy ovládacích prvků aplikace je správné použití <xref:System.Net.Sockets.Socket> tak, aby přijímal data na místních portů nebo se obrátit na vzdálených zařízení pomocí přenosového protokolu na jinou adresu, na základě na hostiteli, číslo portu, a protokol pro přenos soketu.  
  
 Které oprávnění třídy použijete, závisí na typu vaší aplikace. Aplikace, které používají <xref:System.Net.WebRequest> a jeho následníky by měl používat **oprávnění WebPermission** třídy ke správě oprávnění. Aplikace, které používají přístup na úrovni soketu měli používat **SocketPermission** třídy ke správě oprávnění.  
  
 **Oprávnění WebPermission** a **SocketPermission** definovat dvě oprávnění: přijměte a připojení. Přijměte uděluje právo k zodpovězení příchozího spojení ze strany jiné aplikace. Připojení aplikace uděluje práva k navázání připojení k jiné straně.  
  
 Pro **SocketPermission** instance, přijímat znamená, že aplikace může přijmout příchozí spojení na místní přenosu adresu; připojení znamená, že aplikace může připojit k adrese některé přenosu vzdálené (nebo místní).  
  
 Pro **oprávnění WebPermission** instance, přijímat znamená, že aplikace můžete exportovat identifikátor URI řízené **oprávnění WebPermission** World; připojení znamená, že aplikace může použít tento identifikátor URI (ať už jde Vzdálení nebo místní).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení](../../../docs/standard/security/index.md)  
 [Zabezpečení v síťové programování](../../../docs/framework/network-programming/security-in-network-programming.md)
