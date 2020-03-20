---
title: Mechanismy řízení přístupu
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: b423dac4d8324069eb1825666419b23b5afdca63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185490"
---
# <a name="access-control-mechanisms"></a>Mechanismy řízení přístupu
Přístup můžete řídit několika způsoby pomocí Windows Communication Foundation (WCF). Toto téma stručně popisuje různé mechanismy a poskytuje návrhy na to, kdy použít každý; je určen k tomu, aby vám pomohl vybrat správný mechanismus, který chcete použít. Přístupové technologie jsou uvedeny v pořadí podle složitosti. Nejjednodušší je <xref:System.Security.Permissions.PrincipalPermissionAttribute>; nejsložitější je model identity.  
  
 Kromě těchto mechanismů je zosobnění a delegování s WCF vysvětleno v [delegování a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 Slouží <xref:System.Security.Permissions.PrincipalPermissionAttribute> k omezení přístupu k metodě služby. Pokud je atribut použit pro metodu, lze jej použít k vyžádání identity konkrétního volajícího nebo členství ve skupině systému Windows nebo ASP.NET roli. Pokud je klient ověřen pomocí certifikátu X.509, je mu přidělena primární identita, která se skládá z názvu subjektu a kryptografického otisku certifikátu.  
  
 Pomocí <xref:System.Security.Permissions.PrincipalPermissionAttribute> můžete řídit přístup k prostředkům v počítači, ve které je služba spuštěna, a pokud budou uživatelé služby vždy součástí stejné domény systému Windows, ve které je služba spuštěna. Můžete snadno vytvořit skupiny systému Windows, které mají zadané úrovně přístupu (například žádné, jen pro čtení nebo čtení a zápis).  
  
 Další informace o použití atributu naleznete v [tématu How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md). Další informace o identitě naleznete v [tématu Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>poskytovatel členství ASP.NET  
 Funkcí ASP.NET je poskytovatel členství. I když poskytovatel členství není technicky mechanismus řízení přístupu, umožňuje řízení přístupu ke službě omezením sadu možných identit, které mohou přistupovat ke koncovému bodu služby. Funkce členství obsahuje databázi, která může být naplněna kombinacemi uživatelského jména a hesla, které umožňují uživatelům webu vytvářet účty s webem. Chcete-li získat přístup ke službě, která používá poskytovatele členství, musí se uživatel přihlásit pomocí svého uživatelského jména a hesla.  
  
> [!NOTE]
> Nejprve je nutné naplnit databázi pomocí funkce ASP.NET, než ji služba WCF může použít pro účely autorizace.  
  
 Funkci členství můžete použít také v případě, že již máte databázi členství z existujícího webu ASP.NET a chcete povolit stejným uživatelům používat vaši službu, autorizovanou se stejnými uživatelskými jmény a hesly.  
  
 Další informace o použití funkce členství ve službě WCF naleznete v [tématu How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## <a name="aspnet-role-provider"></a>ASP.NET zprostředkovatel role  
 Další funkcí ASP.NET je možnost spravovat autorizaci pomocí rolí. Poskytovatel rolí ASP.NET umožňuje vývojáři vytvářet role pro uživatele a přiřazovat každého uživatele k roli nebo rolím. Stejně jako u poskytovatele členství jsou role a přiřazení uloženy v databázi a mohou být naplněny pomocí nástrojů poskytovaných konkrétní implementací zprostředkovatele rolí ASP.NET. Stejně jako u funkce členství mohou vývojáři WCF použít informace v databázi k autorizaci uživatelů služeb podle rolí. Mohou například použít zprostředkovatele role v `PrincipalPermissionAttribute` kombinaci s mechanismem řízení přístupu popsaným výše.  
  
 Můžete také použít ASP.NET zprostředkovatele rolí, pokud máte existující ASP.NET databázi zprostředkovatele rolí a chcete použít stejnou sadu pravidel a přiřazení uživatelů ve službě WCF.  
  
 Další informace o použití funkce zprostředkovatele rolí naleznete v [tématu Postup: Použití ASP.NET zprostředkovatele rolí se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## <a name="authorization-manager"></a>Správce autorizací  
 Další funkce kombinuje Správce autorizací (AzMan) s poskytovatelem role ASP.NET k autorizaci klientů. Když ASP.NET hostitelem webové služby, azMan lze integrovat do aplikace tak, aby autorizace služby se provádí prostřednictvím AzMan. ASP.NET správce rolí poskytuje rozhraní API, které umožňuje spravovat role aplikace, přidávat a odebírat uživatele z rolí a kontrolovat členství v rolích, ale neumožňuje dotaz, zda je uživatel oprávněn provádět pojmenovanou úlohu nebo operaci. AzMan umožňuje definovat jednotlivé operace a kombinovat je do úkolů. S AZMan, kromě kontroly rolí, můžete také zkontrolovat, zda uživatel může provést úkol. Přiřazení rolí a autorizace úloh lze nakonfigurovat mimo aplikaci nebo provést programově v rámci aplikace. Modul snap-in AzMan administration Microsoft Management Console (MMC) umožňuje správcům měnit úkoly, které může role provádět za běhu, a spravovat členství jednotlivých uživatelů v rolích.  
  
 AzMan a poskytovatele rolí ASP.NET můžete použít také v případě, že již máte přístup k existující instalaci AzMan a chcete autorizovat uživatele služeb pomocí funkcí kombinace AzMan/role provider.  
  
 Další informace o azman a zprostředkovatele rolí ASP.NET naleznete v [tématu How To: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)). Další informace o použití azman a zprostředkovatel role pro služby WCF naleznete v [tématu Postup: Použití ASP.NET zprostředkovatele rolí správce autorizací se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## <a name="identity-model"></a>Identity Model  
 Model identity je sada řešení API, která umožňují spravovat deklarace identity a zásady pro autorizaci klientů. S modelem identity můžete prozkoumat každou deklaraci obsaženou v pověřeních, která volající použil k ověření služby, porovnat deklarace identity se sadou zásad pro službu a udělit nebo odepřít přístup na základě porovnání.  
  
 Model identity použijte, pokud potřebujete jemné řízení a možnost nastavit konkrétní kritéria před udělením přístupu. Například při použití <xref:System.Security.Permissions.PrincipalPermissionAttribute>, kritérium je jednoduše, že identita uživatele je ověřena a patří do určité role. Naproti tomu pomocí modelu identity můžete vytvořit zásadu, která uvádí, že uživatel musí být starší 18 let a má platný řidičský průkaz, než bude moci zobrazit dokument.  
  
 Jedním z příkladů, kde můžete těžit z identity model řízení přístupu založené na deklaraci identity je při použití pověření federace ve scénáři vydaný token. Další informace o federacích a vydaných tokenech naleznete v [tématu Federation and Issueed Tokens](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Další informace o modelu identity naleznete v [tématu Správa deklarací identity a autorizace pomocí modelu identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [Správa deklarací a autorizace s modelem identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
