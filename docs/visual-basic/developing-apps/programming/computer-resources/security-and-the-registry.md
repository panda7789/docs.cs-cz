---
title: Zabezpečení a registr
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 454180207d6432e80d87941d1f329f2a4ea7a801
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345484"
---
# <a name="security-and-the-registry-visual-basic"></a>Zabezpečení a registr (Visual Basic)

This page discusses the security implications of storing data in the registry.  
  
## <a name="permissions"></a>Oprávnění  

 It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).  
  
 Working with the registry may compromise security by allowing inappropriate access to system resources or protected information. To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables. Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry. For more information, see <xref:System.Security.Permissions.RegistryPermission> class.  
  
 Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them. Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.  
  
 Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration. The following table details its members.  
  
|Hodnota|Access to Registry Variables|  
|-----------|----------------------------------|  
|`AllAccess`|Create, read, and write|  
|`Create`|Create|  
|`NoAccess`|No access|  
|`Read`|Číst|  
|`Write`|Write|  
  
## <a name="checking-values-in-registry-keys"></a>Checking Values in Registry Keys  

 When you create a registry value, you need to decide what to do if that value already exists. Another process, perhaps a malicious one, may have already created the value and have access to it. When you put data in the registry value, the data is available to the other process. To prevent this, use the `GetValue` method. It returns `Nothing` if the key does not already exist.  
  
> [!IMPORTANT]
> When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
