---
title: 'Postupy: Zosobnění klienta ve službě'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
ms.openlocfilehash: c15d201a002ec93ff3a83ce1bba9f94ccb6a7b95
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-impersonate-a-client-on-a-service"></a>Postupy: Zosobnění klienta ve službě
Zosobnění klienta ve službě Windows Communication Foundation (WCF) umožňuje službě provádět akce jménem klienta. Pro akce v souladu přístup ovládacího prvku seznam (ACL) kontroly, jako je přístup k adresářů a souborů na počítači, nebo o přístup k databázi systému SQL Server že je kontrola seznamu ACL pro uživatelský účet klienta. Toto téma ukazuje základní kroky potřebné k povolení klientovi v doméně systému Windows nastavení úrovně zosobnění klienta. Pracovní příklad tohoto najdete v tématu [zosobnění klienta](../../../docs/framework/wcf/samples/impersonating-the-client.md). Další informace o zosobnění klienta najdete v tématu [delegace a zosobnění](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
> [!NOTE]
>  Když klient a služba běží na stejném počítači a klient je spuštěn pod účtem systému (to znamená, `Local System` nebo `Network Service`), když zabezpečené relace se naváže stavová tokeny kontext zabezpečení nelze zosobnit klienta. WinForms nebo konzolové aplikace obvykle běží pod aktuálně přihlášený účet tak, aby ve výchozím nastavení se můžou zosobnit účet. Nicméně, pokud je klient [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stránky a že stránky je hostován v [!INCLUDE[iis601](../../../includes/iis601-md.md)] nebo běh služby IIS 7.0, pak klient `Network Service` účet ve výchozím nastavení. Všechny vazby poskytované systémem, které podporují zabezpečených relací ve výchozím nastavení používá token bezstavové kontext zabezpečení. Ale pokud je klient [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stránky a zabezpečených relací s stavová tokeny kontext zabezpečení se používají, nelze jej zosobnit klienta. Další informace o používání stavová tokenů kontextu zabezpečení v zabezpečené relaci najdete v tématu [postupy: vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a>Chcete-li povolit zosobnění klienta z mezipaměti tokenu systému Windows ve službě  
  
1.  Vytvoření služby. Podívejte se kurz tento základní postup, [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
2.  Použít vazbu, která používá ověřování systému Windows a vytvoří relaci, jako například <xref:System.ServiceModel.NetTcpBinding> nebo <xref:System.ServiceModel.WSHttpBinding>.  
  
3.  Při vytváření implementace rozhraní služby, použít <xref:System.ServiceModel.OperationBehaviorAttribute> třída metodu, která vyžaduje zosobnění klienta. Nastavte <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> vlastnost <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a>Nastavení úrovně povolené zosobnění na straně klienta  
  
1.  Vytvoření kódu klienta služby pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Další informace najdete v tématu [přístup k službám pomocí klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).  
  
2.  Po vytvoření klienta WCF, nastavte <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastnost <xref:System.ServiceModel.Security.WindowsClientCredential> třída na jednu z <xref:System.Security.Principal.TokenImpersonationLevel> hodnot výčtu.  
  
    > [!NOTE]
    >  Použít <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, Vyjednané ověřování protokolu Kerberos (někdy nazývané *více větev* nebo *vícekrokový* protokolu Kerberos) se musí použít. Popis toho, jak tuto funkci implementovat, najdete v části [osvědčené postupy pro zabezpečení](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.OperationBehaviorAttribute>  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 [Zosobnění klienta](../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 [Delegace a zosobnění](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
