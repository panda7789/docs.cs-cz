---
title: Podpora pro dotazy
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bed850baca2d06dc0de173ab798da29fb3ec7cc5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="support-for-queries"></a>Podpora pro dotazy
Ukládání Instance pracovního postupu SQL zaznamenává sadu známých vlastností v úložišti. Uživatelé mohou odesílat dotazy na instancí na základě těchto vlastností. Následující seznam obsahuje některé z těchto známých vlastností:  
  
-   **Název lokality.** Název webu, který obsahuje službu.  
  
-   **Relativní cesta.** Cesta aplikace relativně k webu.  
  
-   **Cesta relativní služby.** Cesta relativní k aplikaci služby.  
  
-   **Název služby.** Název služby  
  
-   **Namespace služby.** Název oboru názvů, který služba používá.  
  
-   **Aktuálního počítače.**  
  
-   **Poslední počítač**. Počítač, na kterém byla spuštěna instance pracovního postupu služby čas poslední.  
  
> [!NOTE]
>  Pro scénáře s vlastním hostováním pomocí hostitele služby pracovního postupu naplní se pouze poslední čtyři vlastnosti. Pro scénáře aplikace pracovního postupu se importují pouze poslední vlastnost.  
  
 Modul runtime pracovního postupu poskytuje hodnoty pro první tři vlastnosti. Hostitel služby pracovního postupu poskytuje hodnota **pozastavit důvod** vlastnost. Poskytuje hodnoty pro samotného úložiště Instance pracovního postupu SQL **poslední aktualizovat počítač** vlastnost.  
  
 Funkce úložiště Instance pracovního postupu SQL také umožňuje určit, že vlastní vlastnosti, pro které chcete uložit hodnoty v databázi trvalosti a, které chcete použít v dotazech. Další informace o vlastní povýšení najdete v tématu [rozšiřitelnost úložiště](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).  
  
## <a name="views"></a>zobrazení  
 Instance úložiště obsahuje následující zobrazení. V tématu [schéma databáze trvalost](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) další podrobnosti.  
  
### <a name="the-instances-view"></a>Zobrazení instancí  
 Zobrazení instancí obsahuje následující pole:  
  
1.  **ID**  
  
2.  **PendingTimer**  
  
3.  **Čas vytvoření**  
  
4.  **LastUpdatedTime**  
  
5.  **ServiceDeploymentId**  
  
6.  **SuspensionExceptionName**  
  
7.  **SuspensionReason**  
  
8.  **ActiveBookmarks**  
  
9. **CurrentMachine**  
  
10. **LastMachine**  
  
11. **ExecutionStatus**  
  
12. **IsInitialized.**  
  
13. **IsSuspended**  
  
14. **IsCompleted**  
  
15. **EncodingOption**  
  
16. **ReadWritePrimitiveDataProperties**  
  
17. **WriteOnlyPrimitiveDataProperties**  
  
18. **ReadWriteComplexDataProperties**  
  
19. **WriteOnlyComplexDataProperties**  
  
### <a name="the-servicedeployments-view"></a>Zobrazení ServiceDeployments  
 Zobrazení ServiceDeployments obsahuje následující pole:  
  
1.  **Název webu**  
  
2.  **RelativeServicePath**  
  
3.  **RelativeApplicationPath**  
  
4.  **ServiceName**  
  
5.  **ServiceNamespace**  
  
### <a name="the-instancepromotedproperties-view"></a>Zobrazení InstancePromotedProperties  
 Zobrazení InstancePromotedProperties obsahuje následující pole. Podrobnosti propagovaných vlastností najdete v tématu [rozšiřitelnost úložiště](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) tématu.  
  
1.  **Identifikátor InstanceId**  
  
2.  **EncodingOption**  
  
3.  **PromotionName**  
  
4.  **Hodnota #** (rozsah pole z **Value1** k **Value64**).
