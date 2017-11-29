---
title: "Postupy: Implementace přihlášení uživatele u klientských aplikačních služeb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating users [client application services]
- validation [.NET Framework], client application services
- client application services, authenticate users
ms.assetid: 5431a671-eb02-4e18-a651-24764fccec9a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 909fbaa4e7dc1d384b5085d71cec346bde44cf14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-user-login-with-client-application-services"></a>Postupy: Implementace přihlášení uživatele u klientských aplikačních služeb
Klient aplikačních služeb můžete použít k ověření uživatelů pomocí stávající [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profilu služby. Informace o tom, jak nastavit [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profilu služby najdete v tématu [použití ověřování pomocí formulářů s Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e).  
  
 Následující postupy popisují, jak k ověření uživatelů pomocí služby ověřování, pokud je vaše aplikace nakonfigurovaná pro použití jednoho z poskytovatelů služby ověřování klienta. Další informace najdete v tématu [postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
 Obvykle budete provádět všechny ověřovací prostřednictvím `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metoda. Tato metoda spravuje interakci s ověřovací služby prostřednictvím poskytovatele nakonfigurované ověřování. Další informace najdete v tématu [Přehled klientských aplikačních služeb](../../../docs/framework/common-client-technologies/client-application-services-overview.md).  
  
 Postupy ověřování formulářů vyžadují přístup k spuštěný [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] ověřovací služby. Pokyny k začátku do konce testování klientské aplikace služeb funkce naleznete v tématu [návod: použití klientských aplikačních služeb](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
### <a name="to-authenticate-a-user-with-forms-authentication-using-a-membership-credentials-provider"></a>K ověření uživatele pomocí ověřování pomocí formulářů pomocí přihlašovacích údajů zprostředkovatele členství  
  
1.  Implementace <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> rozhraní. Následující příklad kódu ukazuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> implementace třídy dialogového okna přihlášení odvozené z <xref:System.Windows.Forms.Form?displayProperty=nameWithType>. Dialogové okno obsahuje textová pole pro uživatelské jméno a heslo a zaškrtávací políčko "Zapamatovat uživatele". Při volání zprostředkovatele ověřování klienta <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> se zobrazí v případě metody formuláře. Když uživatel vyplní informace v dialogovém okně přihlášení a klikne na tlačítko OK, zadané hodnoty se vrátí v nové <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> objektu.  
  
     [!code-csharp[ClientApplicationServices#210](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#210)]
     [!code-vb[ClientApplicationServices#210](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#210)]  
  
2.  Volání `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metoda a předejte jí prázdné řetězce jako hodnoty parametru. Když zadáte prázdné řetězce, tato metoda interně volá <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> metoda pro přihlašovací údaje poskytovatele nakonfigurované pro vaši aplikaci. Následující příklad kódu volá tuto metodu za účelem omezení přístupu pro celou aplikaci Windows Forms. Můžete přidat tento kód, aby <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> obslužné rutiny.  
  
     [!code-csharp[ClientApplicationServices#317](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#317)]
     [!code-vb[ClientApplicationServices#317](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#317)]  
  
### <a name="to-authenticate-a-user-with-forms-authentication-without-using-a-membership-credentials-provider"></a>Ověření uživatele pomocí ověřování pomocí formulářů bez použití členství poskytovatel přihlašovacích údajů  
  
-   Volání `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metoda a předejte jí uživatelské jméno a heslo hodnoty načíst od uživatele.  
  
     [!code-csharp[ClientApplicationServices#318](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#318)]
     [!code-vb[ClientApplicationServices#318](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#318)]  
  
### <a name="to-authenticate-a-user-with-windows-authentication"></a>K ověření uživatele pomocí ověřování systému Windows  
  
-   Volání `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> a předáte prázdný řetězce pro parametry. Toto volání metody vždy vrátí `true` a přidá do souboru cookie do mezipaměti souborů cookie uživatele, který obsahuje identitu systému Windows.  
  
     [!code-csharp[ClientApplicationServices#319](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#319)]
     [!code-vb[ClientApplicationServices#319](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#319)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Ukázkový kód v tomto tématu ukazuje nejjednodušší použití ověřování v aplikaci klienta systému Windows. Při volání `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metoda s klientskou aplikaci služby a ověřování pomocí formulářů, ale můžete vyvolat kódu <xref:System.Net.WebException>. To znamená, že ověřovací služby není k dispozici. Příklad způsobu zpracování této výjimky, naleznete v části [návod: použití klientských aplikačních služeb](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Klient aplikačních služeb](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Přehled klientských aplikačních služeb](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [Návod: Použití klientských aplikačních služeb](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [Použití ověřování pomocí formulářů s technologií Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)
