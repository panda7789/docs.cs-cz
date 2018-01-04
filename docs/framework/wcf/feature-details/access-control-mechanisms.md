---
title: "Mechanismy řízení přístupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d856af12269416b3303e617338165771ae4f2b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="access-control-mechanisms"></a>Mechanismy řízení přístupu
Můžete řídit přístup několik způsobem s [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Toto téma stručně popisuje různé mechanismy a poskytuje návrhy na při použití každé; je určena k vám pomohou vybrat správný mechanismus používat. Technologie pro přístup k jsou uvedeny v pořadí podle složitost. Nejjednodušší je <xref:System.Security.Permissions.PrincipalPermissionAttribute>; nejvíce komplexní je modelem Identity.  
  
 Kromě těchto mechanismů, zosobnění a delegování s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je vysvětleno v [delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Se používá k omezení přístupu k metodě služby. Pokud je atribut použitý na metodu, může sloužit požadovat konkrétní volající identity nebo členství ve skupině Windows nebo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role. Pokud klient je ověřování pomocí certifikátu X.509, je uveden primární identitou, která se skládá z název předmětu a kryptografický otisk certifikátu.  
  
 Použití <xref:System.Security.Permissions.PrincipalPermissionAttribute> k řízení přístupu k prostředkům v počítači, který je služba spuštěná, a pokud uživatelé služby budou vždy součástí stejné domény systému Windows, který je služba spuštěná na. Můžete snadno vytvořit skupiny systému Windows, které jste zadali úrovní přístupu (jako jsou none, jen pro čtení, nebo pro čtení a zápis).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pomocí atributu, najdete v tématu [postupy: omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]identity, najdete v části [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>Poskytovatele členství prostředí ASP.NET  
 Funkce [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] je zprostředkovatel členství. I když se zprostředkovatel členství není technicky mechanismu řízení přístupu, umožňuje řízení přístupu ke službě omezením sadu možné identit, kteří mohou přistupovat k koncový bod služby. Funkce členství zahrnuje databázi, která je možné naplnit kombinace uživatelské jméno a heslo, které umožňují uživatelům webu vytvářet účty s lokalitou. Pro přístup k službě, která používá zprostředkovatel členství, musí uživatel přihlásit pomocí své uživatelské jméno a heslo.  
  
> [!NOTE]
>  Musíte nejprve naplnit databázi pomocí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkci před [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby můžete použít pro účely ověření.  
  
 Můžete také použít funkci členství, pokud již máte členství databáze z existující [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webu a chcete povolit stejným uživatelům používat služby oprávnění se stejným uživatelská jména a hesla.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pomocí funkce členství v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] najdete v tématu [postupy: použití poskytovatele členství prostředí ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## <a name="aspnet-role-provider"></a>Zprostředkovatele rolí ASP.NET  
 Další funkce [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] je schopnost spravovat autorizace pomocí rolí. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Zprostředkovatele rolí umožňuje vývojáři k vytvoření role pro uživatele a přiřadit k roli nebo role. Jako u zprostředkovatele členství, role a přiřazení jsou uloženy v databázi a je možné importovat pomocí nástroje poskytované subsystémem pro konkrétní implementaci [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí. Stejně jako u funkce členství [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mohou vývojáři informace v databázi autorizovat uživatele služeb role. Zprostředkovatele rolí se třeba můžou použít v kombinaci s `PrincipalPermissionAttribute` popsané výše mechanismu řízení přístupu.  
  
 Můžete také použít [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí, pokud máte existující [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role zprostředkovatele databáze a chcete použít stejnou sadu pravidel a přiřazení uživatelských ve vaší [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pomocí funkce zprostředkovatele rolí, najdete v tématu [postupy: použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## <a name="authorization-manager"></a>Správce autorizací  
 Další funkcí kombinuje Správce autorizací (AzMan) s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí k autorizaci klientů. Když [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hostitele webové služby, AzMan lze integrovat do aplikace, tak, aby autorizace ke službě se provádí prostřednictvím AzMan. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Správce rolí poskytuje rozhraní API, která umožňuje spravovat aplikační role, přidat, odebrat uživatele z role a zkontrolujte členství v roli, ale neumožňuje vám dotaz, zda je uživatel autorizovaný k provedení úloh s názvem nebo operace. AzMan umožňuje definovat jednotlivé operace a zkombinovat do úlohy. S AZMan kromě kontroly role, můžete také zkontrolovat zda může uživatel provést úlohu. Role ověřování přiřazení a úloh můžete nakonfigurovat mimo aplikaci nebo provést programově v aplikaci. Správa AzMan modul snap-in konzoly Microsoft Management Console (MMC) umožňuje správci ke změně úlohy, které může role provádět v době běhu a spravovat každý uživatel členství rolí.  
  
 Můžete také AzMan a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí, pokud již máte přístup do existující instalace AzMan a autorizovat uživatelé služby pomocí funkce kombinace AzMan nebo roli zprostředkovatele.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]AzMan a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí, najdete v části [postupy: použití Správce autorizací (AzMan) s prostředím ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=88951). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pomocí AzMan a poskytovatel rolí pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, najdete v části [postupy: použití zprostředkovatele rolí Správce autorizací ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## <a name="identity-model"></a>Modelu identity  
 Identity Model je sada rozhraní API, které vám umožní spravovat deklarace identity a zásady, autorizace klientů. S modelem Identity můžete zkontrolovat všechny deklarace obsažené v přihlašovací údaje, které volající používá k ověření samotné služby, porovnání deklarace identity na sadě zásad pro službu a udělit nebo odepřít přístup podle porovnání.  
  
 Pomocí modelu Identity, pokud je třeba přesně řízení a možnost nastavit určitá kritéria před udělením přístupu. Například při použití <xref:System.Security.Permissions.PrincipalPermissionAttribute>, toto kritérium je jednoduše, že identita uživatele je ověřen a patří do určité role. Na rozdíl od použití modelu Identity můžete vytvořit zásadu, která stavů uživatele musí být více než 18 let a má platný ovladač licence dříve, než mohou zobrazení dokumentu.  
  
 Příkladem, kde můžete využívat výhod řízení přístupu na základě deklarace Identity modelu je při použití federační přihlašovací údaje ve scénáři vydaných tokenů. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]federace a vystavené tokeny, najdete v části [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]modelem Identity najdete v části [správa deklarací a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
