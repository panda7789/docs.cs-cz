---
title: Pole s_isDebuggerCheckDisabledForTestPurposes
ms.date: 03/30/2017
ms.technology:
- dotnet-wpf
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
ms.openlocfilehash: f490ccb4675a434e3f3336723e321f256b10093d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149173"
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a><span data-ttu-id="97408-102">Pole s_isDebuggerCheckDisabledForTestPurposes</span><span class="sxs-lookup"><span data-stu-id="97408-102">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>

<span data-ttu-id="97408-103">Tato privátní pole v `System.Windows.Diagnostics.VisualDiagnostics` třída se používá sada Visual Studio k určení, zda bude provedena interní kontroly pro aktivní ladicí program.</span><span class="sxs-lookup"><span data-stu-id="97408-103">This private field in the `System.Windows.Diagnostics.VisualDiagnostics` class is used by Visual Studio to determine whether an internal check for an active debugger will be performed.</span></span>

## <a name="syntax"></a><span data-ttu-id="97408-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97408-104">Syntax</span></span>
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  <span data-ttu-id="97408-105">Rozhraní API v `System.Windows.Diagnostics.VisualDiagnostics` třídy jsou k dispozici, pouze když je aplikace spuštěna v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="97408-105">API's in the `System.Windows.Diagnostics.VisualDiagnostics` class are only available when an application is running under a debugger.</span></span> <span data-ttu-id="97408-106">Nastavte `s_isDebuggerCheckDisabledForTestPurposes` k `true` pro přístup k rozhraní API mimo ladicí program.</span><span class="sxs-lookup"><span data-stu-id="97408-106">Set `s_isDebuggerCheckDisabledForTestPurposes` to `true` to access the APIs outside of a debugger.</span></span>  
>   
>  <span data-ttu-id="97408-107">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="97408-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>  

## <a name="requirements"></a><span data-ttu-id="97408-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97408-108">Requirements</span></span>

<span data-ttu-id="97408-109">**Namespace:** <xref:System.Windows.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="97408-109">**Namespace:** <xref:System.Windows.Diagnostics></span></span>

<span data-ttu-id="97408-110">**Sestavení:** PresentationCore (v PresentationCore.dll)</span><span class="sxs-lookup"><span data-stu-id="97408-110">**Assembly:** PresentationCore (in PresentationCore.dll)</span></span>

<span data-ttu-id="97408-111">**Verze rozhraní .NET framework:** Dostupné od verze 4.6.</span><span class="sxs-lookup"><span data-stu-id="97408-111">**.NET Framework versions:** Available since 4.6.</span></span>