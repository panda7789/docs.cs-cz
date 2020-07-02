---
ms.openlocfilehash: e66a5c2a33a4ab5cf35013c1843936ffd01f90a2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614501"
---
### <a name="serialport-background-thread-exceptions"></a><span data-ttu-id="41efc-101">Portu SerialPort výjimky vlákna na pozadí</span><span class="sxs-lookup"><span data-stu-id="41efc-101">SerialPort background thread exceptions</span></span>

#### <a name="details"></a><span data-ttu-id="41efc-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="41efc-102">Details</span></span>

<span data-ttu-id="41efc-103">Vlákna na pozadí vytvořená pomocí <xref:System.IO.Ports.SerialPort> datových proudů už neukončí proces, když jsou vyvolány výjimky operačního systému.</span><span class="sxs-lookup"><span data-stu-id="41efc-103">Background threads created with <xref:System.IO.Ports.SerialPort> streams no longer terminate the process when OS exceptions are thrown.</span></span> <br/><span data-ttu-id="41efc-104">V aplikacích, které cílí na .NET Framework 4,7 a starších verzí, je proces ukončen, pokud je vyvolána výjimka operačního systému ve vlákně na pozadí vytvořeném pomocí <xref:System.IO.Ports.SerialPort> datového proudu.</span><span class="sxs-lookup"><span data-stu-id="41efc-104">In applications that target the .NET Framework 4.7 and earlier versions, a process is terminated when an operating system exception is thrown on a background thread created with a <xref:System.IO.Ports.SerialPort> stream.</span></span> <br/><span data-ttu-id="41efc-105">V aplikacích, které cílí na .NET Framework 4.7.1 nebo novější verzi, vlákna na pozadí čekají na události operačního systému související s aktivním sériovým portem a v některých případech by mohlo dojít k chybě, jako je například náhlé odebrání sériového portu.</span><span class="sxs-lookup"><span data-stu-id="41efc-105">In applications that target the .NET Framework 4.7.1 or a later version, background threads wait for OS events related to the active serial port and could crash in some cases, such as sudden removal of the serial port.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="41efc-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="41efc-106">Suggestion</span></span>

<span data-ttu-id="41efc-107">U aplikací, které cílí na .NET Framework 4.7.1, se můžete rozhodnout o zpracování výjimek, pokud to není žádoucí, a to tak, že do `<runtime>` části souboru přidáte následující `app.config` :</span><span class="sxs-lookup"><span data-stu-id="41efc-107">For apps that target the .NET Framework 4.7.1, you can opt out of the exception handling if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true" />
</runtime>
```

<span data-ttu-id="41efc-108">Pro aplikace, které jsou cíleny na starší verze .NET Framework, ale běží na .NET Framework 4.7.1 nebo novější, můžete vyjádřit ke zpracování výjimek přidáním následujícího do `<runtime>` části `app.config` souboru:</span><span class="sxs-lookup"><span data-stu-id="41efc-108">For apps that target earlier versions of the .NET Framework but run on the .NET Framework 4.7.1 or later, you can opt in to the exception handling by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false" />
</runtime>
```

| <span data-ttu-id="41efc-109">Name</span><span class="sxs-lookup"><span data-stu-id="41efc-109">Name</span></span>    | <span data-ttu-id="41efc-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="41efc-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="41efc-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="41efc-111">Scope</span></span>   | <span data-ttu-id="41efc-112">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="41efc-112">Minor</span></span>       |
| <span data-ttu-id="41efc-113">Verze</span><span class="sxs-lookup"><span data-stu-id="41efc-113">Version</span></span> | <span data-ttu-id="41efc-114">4.7.1</span><span class="sxs-lookup"><span data-stu-id="41efc-114">4.7.1</span></span>       |
| <span data-ttu-id="41efc-115">Typ</span><span class="sxs-lookup"><span data-stu-id="41efc-115">Type</span></span>    | <span data-ttu-id="41efc-116">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="41efc-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="41efc-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="41efc-117">Affected APIs</span></span>

- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
