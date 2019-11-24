---
title: Izolace sítě pro aplikace z obchodu Microsoft Store
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: 34b8865781079f45a68d3dd1aab7fbd66c703d50
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447416"
---
# <a name="network-isolation-for-windows-store-apps"></a>Izolace sítě pro aplikace z obchodu Microsoft Store
Classes in the <xref:System.Net>,  <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps. When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by the [!INCLUDE[win8](../../../includes/win8-md.md)]. The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.  
  
## <a name="checklist-for-network-isolation"></a>Checklist for Network Isolation  
 Use this checklist to be sure that network isolation is configured for your Windows Store app.  
  
1. Determine the direction of network access requests needed by the app. This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.  
  
2. Determine the type of network resources that the app will communicate with. An app may need to communicate with trusted resources on a Home or Work network. An app might need to communicate with resources on the Internet. An app might need access to both types of network resources.  
  
3. Configure the minimum-required networking isolation capabilities in the app manifest.  
  
4. Deploy and run your app to test it using the network isolation tools provided for troubleshooting.  
  
 For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10)) in the Windows 8.x Store developer documentation.
  
## <a name="see-also"></a>Viz také:

- [Connecting to a web service](https://docs.microsoft.com/previous-versions/windows/apps/hh761504(v=win.10))
- [Guidelines and checklist for network isolation](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10))
- [Quickstart: Connecting using HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781239(v=win.10))
- [How to use HttpClient handlers](https://docs.microsoft.com/previous-versions/windows/apps/hh781241(v=win.10))
- [How to secure HttpClient connections](https://docs.microsoft.com/previous-versions/windows/apps/hh781240(v=win.10))
- [HttpClient Sample](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
