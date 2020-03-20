---
title: Oprávnění pro web a sokety
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
ms.openlocfilehash: d1b993acbf20eac244e596075c3f826bba3211a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046869"
---
# <a name="web-and-socket-permissions"></a>Oprávnění pro web a sokety
Zabezpečení Internetu pro <xref:System.Net> aplikace používající obor <xref:System.Net.WebPermission> názvů <xref:System.Net.SocketPermission> je poskytováno třídami a. Třída **WebPermission** řídí právo aplikace požadovat data z identifikátoru URI nebo obsluhovat identifikátor URI v Síti Internet. Třída **SocketPermission** řídí právo aplikace používat <xref:System.Net.Sockets.Socket> a přijímat data na místním portu nebo kontaktovat vzdálená zařízení pomocí přenosového protokolu na jiné adrese na základě hostitele, čísla portu a přenosového protokolu soketu.  
  
 Třída oprávnění, kterou používáte, závisí na typu aplikace. Aplikace, <xref:System.Net.WebRequest> které používají a jeho následníky by měly používat **WebPermission** třídy ke správě oprávnění. Aplikace, které používají přístup na úrovni soketu, by měly ke správě oprávnění používat třídu **SocketPermission.**  
  
 **WebPermission** a **SocketPermission** definovat dvě oprávnění: přijmout a připojit. Přijmout uděluje aplikaci právo odpovědět na příchozí připojení od jiné strany. Connect uděluje aplikaci právo nazatouji připojení k jiné straně.  
  
 Pro **SocketPermission** instance, přijmout znamená, že aplikace může přijímat příchozí připojení na adresu místního přenosu; znamená, že se aplikace může připojit k některé vzdálené (nebo místní) adrese přenosu.  
  
 Pro instance **WebPermission,** přijmout znamená, že aplikace může exportovat identifikátor URI řízené **WebPermission** do světa; znamená, že aplikace může přistupovat k tomuto identifikátoru URI (ať už je vzdálený nebo místní).  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení](../../standard/security/index.md)
- [Zabezpečení v síťovém programování](security-in-network-programming.md)
