---
title: Oprávnění pro web a sokety
description: Přečtěte si, jak třídy weboprávnění a SocketPermission poskytují zabezpečení Internetu pro používání oboru názvů System.Net v .NET Framework.
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
ms.openlocfilehash: 08ae360e8097f7281631da2a3f9846994dfbf5b6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501895"
---
# <a name="web-and-socket-permissions"></a>Oprávnění pro web a sokety
Internetové zabezpečení pro aplikace, které používají <xref:System.Net> obor názvů, jsou <xref:System.Net.WebPermission> poskytovány <xref:System.Net.SocketPermission> třídami a. Třída **weboprávnění** řídí právo aplikace pro vyžádání dat z identifikátoru URI nebo pro poskytování identifikátoru URI Internetu. Třída **SocketPermission** řídí právo aplikace používat <xref:System.Net.Sockets.Socket> k přijímání dat na místním portu nebo ke kontaktování vzdálených zařízení pomocí přenosového protokolu na jiné adrese, a to na základě hostitele, čísla portu a přenosového protokolu soketu.  
  
 Použitá třída oprávnění závisí na typu vaší aplikace. Aplikace, které používají <xref:System.Net.WebRequest> a její potomci, by měli použít třídu **weboprávnění** ke správě oprávnění. Aplikace, které používají přístup na úrovni soketu, by měly ke správě oprávnění používat třídu **SocketPermission** .  
  
 **Weboprávnění** a **SocketPermission** definují dvě oprávnění: přijmout a připojit. Accept udělí aplikaci právo odpovědět příchozímu připojení z jiné strany. Připojení uděluje aplikaci právo iniciovat připojení k jiné straně.  
  
 U instancí **SocketPermission** Accept (přijmout) znamená, že aplikace může přijmout příchozí připojení na místní transportní adrese; připojit znamená, že se aplikace může připojit k některé vzdálené (nebo místní) transportní adrese.  
  
 U instancí **weboprávnění** Accept (přijmout) znamená, že aplikace může exportovat identifikátor URI řízený **weboprávněními** na světě; možnost připojit znamená, že aplikace má přístup k tomuto identifikátoru URI (ať už se jedná o vzdálené nebo místní).  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení](../../standard/security/index.md)
- [Zabezpečení v síťovém programování](security-in-network-programming.md)
