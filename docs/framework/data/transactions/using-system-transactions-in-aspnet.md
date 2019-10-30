---
title: Použití System.Transactions v ASP.NET
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 2bddebc13897408839e18f42b17a9fbaefdc5b87
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040413"
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="b64df-102">Použití System.Transactions v ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b64df-102">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="b64df-103">Toto téma popisuje, jak můžete úspěšně použít <xref:System.Transactions> v rámci aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b64df-103">This topic describes how you can successfully use <xref:System.Transactions> inside an ASP.NET application.</span></span>

## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="b64df-104">Povolit DistributedTransactionPermission v technologii ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b64df-104">Enable DistributedTransactionPermission in ASP.NET</span></span>
 <span data-ttu-id="b64df-105"><xref:System.Transactions> podporuje částečně důvěryhodné volající a je označen atributem `AllowPartiallyTrustedCallers` (APTCA).</span><span class="sxs-lookup"><span data-stu-id="b64df-105"><xref:System.Transactions> supports partially trusted callers and is marked with the `AllowPartiallyTrustedCallers` attribute (APTCA).</span></span> <span data-ttu-id="b64df-106">Úrovně důvěryhodnosti pro <xref:System.Transactions> jsou definované na základě typů prostředků (například systémové paměti, sdílených prostředků v rámci procesu, prostředků v rámci systému a dalších prostředků), které <xref:System.Transactions> zveřejňuje a úroveň důvěryhodnosti, která by se měla vyžadovat pro přístup k těmto funkcím. prostředky.</span><span class="sxs-lookup"><span data-stu-id="b64df-106">The trust levels for <xref:System.Transactions> are defined based on the types of resources (for example, system memory, shared process-wide resources, system-wide resources, and other resources) that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="b64df-107">V prostředí částečné důvěryhodnosti, můžete použít jiný plně důvěryhodné sestavení pouze transakce v rámci domény aplikace (v takovém případě jediný zdroj chráněn je systémová paměť), pokud má oprávnění <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="b64df-107">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>

 <span data-ttu-id="b64df-108"><xref:System.Transactions.DistributedTransactionPermission> je vyžádané při každém zvýšení správy transakcí, aby je bylo možné spravovat pomocí Microsoft DTC (Distributed Transaction Coordinator) (MSDTC).</span><span class="sxs-lookup"><span data-stu-id="b64df-108"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="b64df-109">Tento druh scénář využívá prostředky celého procesu a zejména globální zdroj, který je vyhrazené místo v protokolu MSDTC.</span><span class="sxs-lookup"><span data-stu-id="b64df-109">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="b64df-110">Příklad toto využití je do databáze nebo aplikace, která používá databázi v rámci služeb, které poskytuje klientské části webu.</span><span class="sxs-lookup"><span data-stu-id="b64df-110">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>

 <span data-ttu-id="b64df-111">ASP.NET má svou vlastní sadu úrovní důvěryhodnosti a přiřazuje konkrétní sadu oprávnění s těmito úrovněmi důvěryhodnosti prostřednictvím souborů zásad.</span><span class="sxs-lookup"><span data-stu-id="b64df-111">ASP.NET has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> <span data-ttu-id="b64df-112">Další informace najdete v tématu [úrovně důvěryhodnosti ASP.NET a soubory zásad](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b64df-112">For more information, see [ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span></span> <span data-ttu-id="b64df-113">Při první instalaci Windows SDK nejsou k <xref:System.Transactions.DistributedTransactionPermission>přidruženy žádné výchozí soubory zásad ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b64df-113">When you initially install the Windows SDK, none of the default ASP.NET policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="b64df-114">V takovém případě, když je vaše transakce v aplikaci ASP.NET eskalacá, aby se spravovala pomocí služby MSDTC, eskalace se nezdařila s <xref:System.Security.SecurityException>em při náročné <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="b64df-114">As such, when your transaction in an ASP.NET application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="b64df-115">Chcete-li povolit eskalaci transakce v prostředí ASP.NET s částečným vztahem důvěryhodnosti, je třeba udělit <xref:System.Transactions.DistributedTransactionPermission> ve stejné výchozí úrovni důvěryhodnosti jako <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="b64df-115">To enable transaction escalation in an ASP.NET partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="b64df-116">Můžete buď nakonfigurovat vlastní vlastní úroveň důvěryhodnosti a soubor zásad pro podporu, nebo můžete upravit výchozí soubory zásad, které jsou **Web_hightrust. config** a **web_mediumtrust. config**.</span><span class="sxs-lookup"><span data-stu-id="b64df-116">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>

 <span data-ttu-id="b64df-117">Chcete-li upravit soubory zásad, přidejte `SecurityClass` element pro `DistributedTransactionPermission` do prvku `SecurityClasses` pod prvkem `PolicyLevel` a přidejte odpovídající `IPermission` prvek v rámci ASP.NET `NamedPermissionSet` pro System. Transactions.</span><span class="sxs-lookup"><span data-stu-id="b64df-117">To modify the policy files, add a `SecurityClass` element for `DistributedTransactionPermission` to the `SecurityClasses` element under the `PolicyLevel` element and add a corresponding `IPermission` element under the ASP.NET `NamedPermissionSet` for System.Transactions.</span></span> <span data-ttu-id="b64df-118">Následující konfigurační soubor ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="b64df-118">The following configuration file demonstrates this.</span></span>

```xml
<SecurityClasses>
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
...
</SecurityClasses>

<PermissionSet
  class="NamedPermissionSet"
  version="1"
  Name="ASP.Net">
     <IPermission
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
        version="1"
        Unrestricted="true"
     />
...
</PermissionSet>
```

 <span data-ttu-id="b64df-119">Další informace o zásadách zabezpečení ASP.NET naleznete v tématu [Element securityPolicy (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b64df-119">For more information about ASP.NET security policy, see [securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span></span>

## <a name="dynamic-compilation"></a><span data-ttu-id="b64df-120">Dynamická kompilace</span><span class="sxs-lookup"><span data-stu-id="b64df-120">Dynamic Compilation</span></span>
 <span data-ttu-id="b64df-121">Pokud chcete importovat a používat <xref:System.Transactions> v aplikaci ASP.NET, která je dynamicky kompilována v přístupu, měli byste umístit odkaz na <xref:System.Transactions> sestavení v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b64df-121">If you want to import and use <xref:System.Transactions> in an ASP.NET application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="b64df-122">Odkaz konkrétně by měl být přidán do oddílu `compilation/assemblies` výchozího kořenového konfiguračního souboru **Web. config** nebo konkrétního konfiguračního souboru webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="b64df-122">Specifically, the reference should be added under the `compilation/assemblies` section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="b64df-123">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="b64df-123">The following example demonstrates this.</span></span>

```xml
<configuration>
   <system.web>
      <compilation>
         <assemblies>
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
         </assemblies>
      </compilation>
   </system.web>
</configuration>
```

 <span data-ttu-id="b64df-124">Další informace najdete v tématu [Přidání elementu pro sestavení pro kompilaci (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b64df-124">For more information, see [add Element for assemblies for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="b64df-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b64df-125">See also</span></span>

- <span data-ttu-id="b64df-126">[ASP.NET úrovně důvěryhodnosti a soubory zásad](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b64df-126">[ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span></span>
- <span data-ttu-id="b64df-127">[securityPolicy – element (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b64df-127">[securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span></span>
- [<span data-ttu-id="b64df-128">Eskalace správy transakce</span><span class="sxs-lookup"><span data-stu-id="b64df-128">Transaction Management Escalation</span></span>](transaction-management-escalation.md)
