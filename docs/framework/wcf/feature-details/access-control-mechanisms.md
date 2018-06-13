---
title: Mechanismy řízení přístupu
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: 57ead53dd9e6bc1b2e3624791c7cc0c7d437cd7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493162"
---
# <a name="access-control-mechanisms"></a>Mechanismy řízení přístupu
Můžete řídit přístup způsobem několik Windows Communication Foundation (WCF). Toto téma stručně popisuje různé mechanismy a poskytuje návrhy na při použití každé; je určena k vám pomohou vybrat správný mechanismus používat. Technologie pro přístup k jsou uvedeny v pořadí podle složitost. Nejjednodušší je <xref:System.Security.Permissions.PrincipalPermissionAttribute>; nejvíce komplexní je modelem Identity.  
  
 Kromě těchto mechanismů zosobnění a delegování s použitím technologie WCF je vysvětleno v [delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Se používá k omezení přístupu k metodě služby. Pokud je atribut použitý na metodu, může sloužit požadovat konkrétní volající identity nebo členství ve skupině Windows nebo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role. Pokud klient je ověřování pomocí certifikátu X.509, je uveden primární identitou, která se skládá z název předmětu a kryptografický otisk certifikátu.  
  
 Použití <xref:System.Security.Permissions.PrincipalPermissionAttribute> k řízení přístupu k prostředkům v počítači, který je služba spuštěná, a pokud uživatelé služby budou vždy součástí stejné domény systému Windows, který je služba spuštěná na. Můžete snadno vytvořit skupiny systému Windows, které jste zadali úrovní přístupu (jako jsou none, jen pro čtení, nebo pro čtení a zápis).  
  
 Další informace o používání atribut najdete v tématu [postupy: omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md). Další informace o identitě najdete v tématu [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>Poskytovatele členství prostředí ASP.NET  
 Funkce [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] je zprostředkovatel členství. I když se zprostředkovatel členství není technicky mechanismu řízení přístupu, umožňuje řízení přístupu ke službě omezením sadu možné identit, kteří mohou přistupovat k koncový bod služby. Funkce členství zahrnuje databázi, která je možné naplnit kombinace uživatelské jméno a heslo, které umožňují uživatelům webu vytvářet účty s lokalitou. Pro přístup k službě, která používá zprostředkovatel členství, musí uživatel přihlásit pomocí své uživatelské jméno a heslo.  
  
> [!NOTE]
>  Musíte nejprve naplnit databázi pomocí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkcí služby WCF mohli používat pro účely ověření.  
  
 Můžete také použít funkci členství, pokud již máte členství databáze z existující [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webu a chcete povolit stejným uživatelům používat služby oprávnění se stejným uživatelská jména a hesla.  
  
 Další informace o používání funkce členství ve službě WCF najdete v tématu [postupy: použití poskytovatele členství prostředí ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## <a name="aspnet-role-provider"></a>Zprostředkovatele rolí ASP.NET  
 Další funkce [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] je schopnost spravovat autorizace pomocí rolí. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Zprostředkovatele rolí umožňuje vývojáři k vytvoření role pro uživatele a přiřadit k roli nebo role. Jako u zprostředkovatele členství, role a přiřazení jsou uloženy v databázi a je možné importovat pomocí nástroje poskytované subsystémem pro konkrétní implementaci [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí. Jako funkce členství s WCF mohou vývojáři informace v databázi autorizovat uživatele služeb role. Zprostředkovatele rolí se třeba můžou použít v kombinaci s `PrincipalPermissionAttribute` popsané výše mechanismu řízení přístupu.  
  
 Můžete také [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí, pokud máte existující [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role zprostředkovatele databáze a chcete použít stejnou sadu pravidel a přiřazení uživatelských ve službě WCF.  
  
 Další informace o používání funkcí zprostředkovatele rolí, najdete v části [postupy: použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## <a name="authorization-manager"></a>Správce autorizací  
 Další funkcí kombinuje Správce autorizací (AzMan) s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí k autorizaci klientů. Když [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hostitele webové služby, AzMan lze integrovat do aplikace, tak, aby autorizace ke službě se provádí prostřednictvím AzMan. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Správce rolí poskytuje rozhraní API, která umožňuje spravovat aplikační role, přidat, odebrat uživatele z role a zkontrolujte členství v roli, ale neumožňuje vám dotaz, zda je uživatel autorizovaný k provedení úloh s názvem nebo operace. AzMan umožňuje definovat jednotlivé operace a zkombinovat do úlohy. S AZMan kromě kontroly role, můžete také zkontrolovat zda může uživatel provést úlohu. Role ověřování přiřazení a úloh můžete nakonfigurovat mimo aplikaci nebo provést programově v aplikaci. Správa AzMan modul snap-in konzoly Microsoft Management Console (MMC) umožňuje správci ke změně úlohy, které může role provádět v době běhu a spravovat každý uživatel členství rolí.  
  
 Můžete také AzMan a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí, pokud již máte přístup do existující instalace AzMan a autorizovat uživatelé služby pomocí funkce kombinace AzMan nebo roli zprostředkovatele.  
  
 Další informace o AzMan a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí, najdete v části [postupy: použití Správce autorizací (AzMan) s prostředím ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=88951). Další informace o používání AzMan a poskytovatel rolí pro služby WCF najdete v tématu [postupy: použití zprostředkovatele rolí Správce autorizací ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## <a name="identity-model"></a>Modelu identity  
 Identity Model je sada rozhraní API, které vám umožní spravovat deklarace identity a zásady, autorizace klientů. S modelem Identity můžete zkontrolovat všechny deklarace obsažené v přihlašovací údaje, které volající používá k ověření samotné služby, porovnání deklarace identity na sadě zásad pro službu a udělit nebo odepřít přístup podle porovnání.  
  
 Pomocí modelu Identity, pokud je třeba přesně řízení a možnost nastavit určitá kritéria před udělením přístupu. Například při použití <xref:System.Security.Permissions.PrincipalPermissionAttribute>, toto kritérium je jednoduše, že identita uživatele je ověřen a patří do určité role. Na rozdíl od použití modelu Identity můžete vytvořit zásadu, která stavů uživatele musí být více než 18 let a má platný ovladač licence dříve, než mohou zobrazení dokumentu.  
  
 Příkladem, kde můžete využívat výhod řízení přístupu na základě deklarace Identity modelu je při použití federační přihlašovací údaje ve scénáři vydaných tokenů. Další informace o federace a vystavené tokeny najdete v tématu [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Další informace o modelu Identity najdete v tématu [správa deklarací a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
