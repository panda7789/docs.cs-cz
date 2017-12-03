---
title: "Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute"
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
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ddfb7b343bf4eb551b5029c538d29f104698adf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a>Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute
Řízení přístupu k prostředkům v počítači domény systému Windows je úloha základní zabezpečení. Například pouze určité uživatelé by měli být schopní zobrazit citlivá data, jako jsou informace o mzdách. Toto téma vysvětluje, jak omezit přístup k metodě pomocí vyžadování, které uživatel patří do předdefinované skupiny. Pracovní vzorek, najdete v části [autorizace přístupu k operacím služby](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).  
  
 Úloha se skládá z dva samostatné postupy. První vytvoří skupinu a naplní s uživateli. Druhá <xref:System.Security.Permissions.PrincipalPermissionAttribute> třídy zadejte skupinu.  
  
### <a name="to-create-a-windows-group"></a>Chcete-li vytvořit skupiny systému Windows  
  
1.  Otevřete **Správa počítače** konzoly.  
  
2.  V levém panelu klikněte na **místní uživatelé a skupiny**.  
  
3.  Klikněte pravým tlačítkem na **skupiny**a klikněte na tlačítko **nová skupina**.  
  
4.  V **název skupiny** zadejte název nové skupiny.  
  
5.  V **popis** zadejte popis nové skupiny.  
  
6.  Klikněte **přidat** tlačítko Přidat nové členy do skupiny.  
  
7.  Pokud jste sami přidali do skupiny a chcete otestovat následující kód, je nutné odhlásit počítač a znovu přihlásit, aby se ve skupině obsaženy.  
  
### <a name="to-demand-user-membership"></a>Vyžádání uživatele členství  
  
1.  Otevřete [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] soubor kódu, který obsahuje kód kontraktu implementovaná službu. [!INCLUDE[crabout](../../../includes/crabout-md.md)]implementace kontraktu, najdete v části [implementace kontraktů služby](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
2.  Použít <xref:System.Security.Permissions.PrincipalPermissionAttribute> atribut každá metoda, která musí být omezeno na konkrétní skupinu. Nastavte <xref:System.Security.Permissions.SecurityAttribute.Action%2A> vlastnost <xref:System.Security.Permissions.SecurityAction.Demand> a <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> vlastnost na název skupiny. Příklad:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  Pokud použijete <xref:System.Security.Permissions.PrincipalPermissionAttribute> atribut kontraktu <xref:System.Security.SecurityException> bude vyvolána. Lze použít pouze atribut na úrovni metody.  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a>Použití certifikátu pro řízení přístupu k metodě  
 Můžete také `PrincipalPermissionAttribute` třída k řízení přístupu k metodu, pokud je certifikát typu pověření klienta. Chcete-li to provést, musí mít předmětu a kryptografický otisk certifikátu.  
  
 Chcete-li prozkoumat certifikát pro jeho vlastnosti, přečtěte si téma [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md). Hodnota kryptografického otisku, najdete v tématu [postupy: načtení kryptografického otisku certifikátu](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
#### <a name="to-control-access-using-a-certificate"></a>Pokud chcete řídit přístup pomocí certifikátu  
  
1.  Použít <xref:System.Security.Permissions.PrincipalPermissionAttribute> třída metodu, kterou chcete omezit přístup k.  
  
2.  Nastavení akce atributu <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.  
  
3.  Nastavte `Name` vlastnost na řetězec, který se skládá z název předmětu a kryptografický otisk certifikátu. Oddělte dvě hodnoty středník a mezeru, jak je znázorněno v následujícím příkladu:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4.  Nastavte <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> vlastnost <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> jak je znázorněno v následujícím příkladu konfigurace:  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Nastavení této hodnoty na `UseAspNetRoles` znamená, že `Name` vlastnost `PrincipalPermissionAttribute` se použije k provádění porovnání řetězců. Když je certifikát použit jako pověření klienta, ve výchozím nastavení [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zřetězí běžný název certifikátu a kryptografický otisk středníkem k vytvoření jedinečné hodnoty pro primární identitu klienta. S `UseAspNetRoles` nastavit jako `PrincipalPermissionMode` na službu, tato hodnota primární identity se porovná s `Name` hodnotu vlastnosti k určení přístupová práva uživatele.  
  
     Můžete taky při vytváření samoobslužné hostovanou službu, nastavte <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> vlastností v kódu, jak je znázorněno v následujícím kódu:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.SecurityAction.Demand>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>  
 [Autorizace přístupu k operacím služby](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [Přehled zabezpečení](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md)
