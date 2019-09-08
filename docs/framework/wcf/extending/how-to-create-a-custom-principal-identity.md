---
title: 'Postupy: Vytvoření vlastní identity objektu zabezpečení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IPrincipal
- IAuthorizationPolicy
- PrincipalPermissionMode
- PrincipalPermissionAttribute
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
ms.openlocfilehash: 05a90c4020f225414b21e82684e46b3c2abda010
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797067"
---
# <a name="how-to-create-a-custom-principal-identity"></a>Postupy: Vytvoření vlastní identity objektu zabezpečení
<xref:System.Security.Permissions.PrincipalPermissionAttribute> Je deklarativní způsob řízení přístupu k metodám služby. Při použití tohoto atributu <xref:System.ServiceModel.Description.PrincipalPermissionMode> výčet Určuje režim pro provádění kontrol autorizace. Pokud je tento režim nastaven na <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, umožňuje uživateli zadat vlastní <xref:System.Security.Principal.IPrincipal> třídu vrácenou <xref:System.Threading.Thread.CurrentPrincipal%2A> vlastností. Toto téma ukazuje scénář, kdy <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> se používá v kombinaci s vlastními zásadami autorizace a vlastním objektem zabezpečení.  
  
 Další informace o použití <xref:System.Security.Permissions.PrincipalPermissionAttribute>naleznete v tématu [How to: Omezte přístup pomocí třídy](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)PrincipalPermissionAttribute.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pro zkompilování kódu jsou potřeba odkazy na následující obory názvů:  
  
- <xref:System>  
  
- <xref:System.Collections.Generic>  
  
- <xref:System.Security.Permissions>  
  
- <xref:System.Security.Principal>  
  
- <xref:System.Threading>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Description>  
  
- <xref:System.IdentityModel.Claims>  
  
- <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Postupy: Použití poskytovatele rolí ASP.NET se službou](../feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)
