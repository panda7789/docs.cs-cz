---
title: s_isDebuggerCheckDisabledForTestPurposes pole
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
robots: noindex,nofollow
ms.openlocfilehash: fbbd8d33ea163efaad1417ab4a1435df729e4897
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752198"
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a><span data-ttu-id="af119-102">s_isDebuggerCheckDisabledForTestPurposes pole</span><span class="sxs-lookup"><span data-stu-id="af119-102">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>

<span data-ttu-id="af119-103">Toto pole privátní v `System.Windows.Diagnostics.VisualDiagnostics` třída se používá Visual Studio k určení, zda se provede interní kontrola pro aktivní ladicí program.</span><span class="sxs-lookup"><span data-stu-id="af119-103">This private field in the `System.Windows.Diagnostics.VisualDiagnostics` class is used by Visual Studio to determine whether an internal check for an active debugger will be performed.</span></span>

## <a name="syntax"></a><span data-ttu-id="af119-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af119-104">Syntax</span></span>
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  <span data-ttu-id="af119-105">Rozhraní API v `System.Windows.Diagnostics.VisualDiagnostics` třídy jsou dostupné, jenom když aplikace běží pod ladicí program.</span><span class="sxs-lookup"><span data-stu-id="af119-105">API's in the `System.Windows.Diagnostics.VisualDiagnostics` class are only available when an application is running under a debugger.</span></span> <span data-ttu-id="af119-106">Nastavit `s_isDebuggerCheckDisabledForTestPurposes` k `true` pro přístup k rozhraní API mimo ladicí program.</span><span class="sxs-lookup"><span data-stu-id="af119-106">Set `s_isDebuggerCheckDisabledForTestPurposes` to `true` to access the APIs outside of a debugger.</span></span>  
>   
>  <span data-ttu-id="af119-107">Společnost Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="af119-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>  

## <a name="requirements"></a><span data-ttu-id="af119-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af119-108">Requirements</span></span>

<span data-ttu-id="af119-109">**Namespace:** <xref:System.Windows.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="af119-109">**Namespace:** <xref:System.Windows.Diagnostics></span></span>

<span data-ttu-id="af119-110">**Sestavení:** PresentationCore (v knihovně PresentationCore.dll)</span><span class="sxs-lookup"><span data-stu-id="af119-110">**Assembly:** PresentationCore (in PresentationCore.dll)</span></span>

<span data-ttu-id="af119-111">**Verze rozhraní .NET framework:** dostupné od verze 4.6.</span><span class="sxs-lookup"><span data-stu-id="af119-111">**.NET Framework versions:** Available since 4.6.</span></span>
