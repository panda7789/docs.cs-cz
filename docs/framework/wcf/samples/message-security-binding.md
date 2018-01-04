---
title: "Vazby zabezpečení zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4570ce7-864e-461b-85d8-0f7bcc53c2c8
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f0c8b125d3fc313dca4140b871ccea8165329fda
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-binding"></a>Vazby zabezpečení zpráv
Tato část obsahuje příklady vysvětlující vazby zabezpečení zpráv ve službách systému Windows v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zabezpečení zpráv s anonymní metodou](../../../../docs/framework/wcf/samples/message-security-anonymous.md)  
 Tento příklad ukazuje, jak implementovat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace používající zabezpečení na úrovni zpráv bez jakéhokoli ověřování klienta, ale která vyžaduje server ověřování pomocí certifikátu X.509 serveru.  
  
 [Certifikát zabezpečení zpráv](../../../../docs/framework/wcf/samples/message-security-certificate.md)  
 Tento příklad znázorňuje implementaci aplikace, která používá WS-zabezpečení X.509 v3 s ověřováním pomocí certifikátu pro klienta a vyžaduje ověření serveru pomocí serveru certifikát X.509 v3.  
  
 [Zabezpečení zpráv s uživatelským jménem](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
 Tento příklad znázorňuje implementaci aplikace, která využívá WS-zabezpečení pomocí uživatelského jména ověřování klienta a vyžaduje server ověřování pomocí certifikátu x.509 v3 serveru.  
  
 [Zabezpečení zpráv – Windows](../../../../docs/framework/wcf/samples/message-security-windows.md)  
 Tento příklad ukazuje, jak nakonfigurovat <xref:System.ServiceModel.WSHttpBinding> vazba k zabezpečení na úrovni zpráv pomocí ověřování systému Windows.
