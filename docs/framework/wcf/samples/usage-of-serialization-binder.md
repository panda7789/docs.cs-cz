---
title: Použití vazače serializace
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 10900950b935b484053fe8e37263f0dfc25eba99
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348461"
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="7606e-102">Použití vazače serializace</span><span class="sxs-lookup"><span data-stu-id="7606e-102">Usage of Serialization Binder</span></span>
<span data-ttu-id="7606e-103">Tento příklad ukazuje způsob použití <xref:System.Runtime.Serialization.SerializationBinder> chcete změnit verzi obecného typu, pokud je serializována.</span><span class="sxs-lookup"><span data-stu-id="7606e-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="7606e-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="7606e-104">Demonstrates</span></span>  
 <span data-ttu-id="7606e-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="7606e-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="7606e-106">Diskuse</span><span class="sxs-lookup"><span data-stu-id="7606e-106">Discussion</span></span>  
 <span data-ttu-id="7606e-107">Tento příklad ukazuje, jak dvě entity, jsou cílení na různé verze rozhraní .NET Framework mohou komunikovat pomocí binární formátovací modul a vazače serializace.</span><span class="sxs-lookup"><span data-stu-id="7606e-107">This sample shows how two entities that are targeting different versions of the .NET Framework can communicate using the binary formatter and the serialization binder.</span></span>  
  
<span data-ttu-id="7606e-108">Tato ukázka byla vyvinutá pomocí vzdálené komunikace .NET.</span><span class="sxs-lookup"><span data-stu-id="7606e-108">This sample was developed using .NET Remoting.</span></span> <span data-ttu-id="7606e-109">Skládá se ze serveru cílení [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], který implementuje kontrakt s obecných typů a různí klienti, jeden cílení rozhraní .NET Framework 2.0 a cílí na jinou [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7606e-109">It consists of a server targeting [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], which implements a contract with generic types, and two different clients, one targeting .NET Framework 2.0 and another targeting [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span></span>  
  
 <span data-ttu-id="7606e-110">Server připojí <xref:System.Runtime.Serialization.SerializationBinder> na binární formátovací modul, abyste mohli změnit verzi typy odpovídajícím způsobem na serializace, takže oba klienti může deserializovat tyto typy správně.</span><span class="sxs-lookup"><span data-stu-id="7606e-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7606e-111">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="7606e-111">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="7606e-112">Ke spuštění klienta, klikněte pravým tlačítkem na řešení, SBGenericsVTS (6 projektů) a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="7606e-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2. <span data-ttu-id="7606e-113">V **společné vlastnosti**vyberte **spouštěný projekt**a pak vyberte **více projektů po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="7606e-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="7606e-114">Vyberte **Server** první, potom **Client20** a potom **Client40**.</span><span class="sxs-lookup"><span data-stu-id="7606e-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="7606e-115">Vyberte **Start** akce do těchto tří projektů a ponechte zbývající nastavení **žádný**.</span><span class="sxs-lookup"><span data-stu-id="7606e-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4. <span data-ttu-id="7606e-116">Klikněte na tlačítko **OK** a potom stiskněte klávesu F5 ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="7606e-116">Click **OK** and then press F5 to run the sample.</span></span>
