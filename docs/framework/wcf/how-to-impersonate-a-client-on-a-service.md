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
ms.openlocfilehash: d58f25f279bf2baa1caa7744cea94b909f48866f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002063"
---
# <a name="how-to-impersonate-a-client-on-a-service"></a>Postupy: Zosobnění klienta ve službě
Zosobnění klienta ve službě Windows Communication Foundation (WCF) umožňuje službě a provádět akce jménem klienta. Pro akce v souladu s přístup ovládacího prvku seznam (ACL) kontroly, jako je například přístup k adresářů a souborů na počítači nebo přístup k databázi serveru SQL Server že je kontrola seznamu ACL pro uživatelský účet klienta. Toto téma popisuje základní kroky potřebné k povolení klientům v doméně Windows nastavte úroveň zosobnění klienta. Funkční příklad tohoto objektu, najdete v části [zosobnění klienta](../../../docs/framework/wcf/samples/impersonating-the-client.md). Další informace o zosobnění klienta najdete v tématu [delegace a zosobnění](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
> [!NOTE]
>  Když klient a služba běží na stejném počítači a klient je spuštěn pod účtem systému (to znamená `Local System` nebo `Network Service`), nelze zosobnit klienta, po vytvoření zabezpečené relace pomocí stavového tokenů kontextu zabezpečení. WinForms nebo konzolové aplikace obvykle běží pod aktuálně přihlášený účet tak, aby ve výchozím nastavení se můžou zosobnit účet. Nicméně, pokud je klient [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stránky a této stránce je hostovaná v [!INCLUDE[iis601](../../../includes/iis601-md.md)] nebo IIS 7.0, pak klient spouštěna `Network Service` účet ve výchozím nastavení. Ve výchozím nastavení všechny vazby poskytované systémem, které podporují zabezpečených relací pomocí bezstavové token kontextu zabezpečení. Nicméně pokud je klient [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stránky a zabezpečené relace pomocí stavového tokenů kontextu zabezpečení se používají, nelze zosobnit klienta. Další informace o používání stavové tokenů kontextu zabezpečení v zabezpečené relaci, najdete v části [jak: Vytvoření kontextu zabezpečení pro zabezpečenou relaci Token](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a>Chcete-li povolit zosobnění klienta z Windows token v mezipaměti ve službě  
  
1. Vytvořte službu. Kurz tento základní postup najdete v tématu [kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
2. Použít vazbu, která používá ověřování Windows a vytvoří relaci, jako například <xref:System.ServiceModel.NetTcpBinding> nebo <xref:System.ServiceModel.WSHttpBinding>.  
  
3. Při vytváření implementací rozhraní služby se vztahují <xref:System.ServiceModel.OperationBehaviorAttribute> třídy v metodě, která vyžaduje zosobnění klienta. Nastavte <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> vlastnost <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a>Nastavení úrovně povolené zosobnění klienta  
  
1. Vytvoření kódu klienta služby pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Další informace najdete v tématu [přístup ke službám pomocí klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).  
  
2. Po vytvoření klienta WCF <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastnost <xref:System.ServiceModel.Security.WindowsClientCredential> třídy do jednoho z <xref:System.Security.Principal.TokenImpersonationLevel> hodnot výčtu.  
  
    > [!NOTE]
    >  Použití <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, vyjednávaný ověřování protokolu Kerberos (říká se jim *více fáze* nebo *vícekrokového* protokolu Kerberos) musí být použita. Popis toho, jak toto implementovat, najdete v části [osvědčené postupy pro zabezpečení](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.Security.Principal.TokenImpersonationLevel>
- [Zosobnění klienta](../../../docs/framework/wcf/samples/impersonating-the-client.md)
- [Delegace a zosobnění](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
