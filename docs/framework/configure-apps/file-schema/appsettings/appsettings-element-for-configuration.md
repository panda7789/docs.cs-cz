---
title: <appSettings> – element pro <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: e1f285aae10a89fa49846534d5b47e15920294ea
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452276"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="81593-102">\<Element appSettings > pro \<konfigurace ></span><span class="sxs-lookup"><span data-stu-id="81593-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="81593-103">Obsahuje vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="81593-103">Contains custom application settings.</span></span> <span data-ttu-id="81593-104">Toto je předdefinovaný konfigurační oddíl poskytnutý .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81593-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="81593-105">[**konfigurační >\<** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="81593-105">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="81593-106">&nbsp;&nbsp; **\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="81593-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="81593-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81593-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="81593-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="81593-108">Attribute</span></span>

|           | <span data-ttu-id="81593-109">Popis</span><span class="sxs-lookup"><span data-stu-id="81593-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="81593-110">**souborů**</span><span class="sxs-lookup"><span data-stu-id="81593-110">**file**</span></span>  | <span data-ttu-id="81593-111">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="81593-111">Optional attribute.</span></span><br><br><span data-ttu-id="81593-112">Určuje relativní cestu k externímu souboru, který obsahuje vlastní nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="81593-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="81593-113">Zadaný soubor obsahuje stejný druh nastavení, které jsou zadány v **\<přidat >** , **\<odebrat >** a **\<odstranit >** prvky a jako tyto prvky používá stejný formát dvojice klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="81593-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="81593-114">Zadaná cesta je relativní vzhledem k hlavnímu konfiguračnímu souboru.</span><span class="sxs-lookup"><span data-stu-id="81593-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="81593-115">V případě aplikace model Windows Forms se jedná o binární složku (například */bin/Debug*), nikoli o umístění konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="81593-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="81593-116">Pro aplikace webových formulářů je cesta relativní k kořenovému adresáři aplikace, kde je umístěn soubor *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="81593-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="81593-117">Modul runtime ignoruje atribut, pokud zadaný soubor nelze nalézt.</span><span class="sxs-lookup"><span data-stu-id="81593-117">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="81593-118">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="81593-118">Parent element</span></span>

|     | <span data-ttu-id="81593-119">Popis</span><span class="sxs-lookup"><span data-stu-id="81593-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="81593-120">**konfigurace\<>** Objekt</span><span class="sxs-lookup"><span data-stu-id="81593-120">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="81593-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81593-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="81593-122">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="81593-122">Child elements</span></span>

|     | <span data-ttu-id="81593-123">Popis</span><span class="sxs-lookup"><span data-stu-id="81593-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="81593-124"> **\<přidat >** </span><span class="sxs-lookup"><span data-stu-id="81593-124">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="81593-125">Přidá vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="81593-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="81593-126"> **\<vymazat >** </span><span class="sxs-lookup"><span data-stu-id="81593-126">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="81593-127">Vymaže všechna dříve definovaná nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="81593-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="81593-128"> **\<odebrat >** </span><span class="sxs-lookup"><span data-stu-id="81593-128">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="81593-129">Odebere dříve definované nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="81593-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="81593-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81593-130">Remarks</span></span>

<span data-ttu-id="81593-131">Element **\<appSettings >** ukládá vlastní informace o konfiguraci aplikace, například připojovací řetězce k databázi, cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="81593-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="81593-132">Páry klíč/hodnota zadané v elementu **\<appSettings >** jsou k dispozici v kódu pomocí třídy <xref:System.Configuration.ConfigurationSettings>.</span><span class="sxs-lookup"><span data-stu-id="81593-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="81593-133">Atribut **File** lze použít v prvku **\<appSettings >** elementu *Web. config* a konfiguračních souborů aplikace.</span><span class="sxs-lookup"><span data-stu-id="81593-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="81593-134">Tento atribut určuje konfigurační soubor, který poskytuje další nastavení nebo přepisuje nastavení zadané v prvku **\<appSettings >** .</span><span class="sxs-lookup"><span data-stu-id="81593-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="81593-135">Atribut **File** lze použít ve scénářích vývoje týmu správy zdrojového kódu, například když chce uživatel přepsat nastavení projektu zadané v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="81593-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="81593-136">Konfigurační soubory určené atributem **souboru** musí mít kořenový uzel **\<appSettings >** spíše než **\<> Konfigurace**.</span><span class="sxs-lookup"><span data-stu-id="81593-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="81593-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="81593-137">Example</span></span>

<span data-ttu-id="81593-138">Následující příklad ukazuje soubor nastavení externí aplikace (*Custom. config*), který definuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="81593-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="81593-139">Následující příklad ukazuje konfigurační soubor aplikace, který využívá nastavení v souboru externího nastavení a nastavuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="81593-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="81593-140">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="81593-140">Configuration file</span></span>

<span data-ttu-id="81593-141">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="81593-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="81593-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="81593-142">See also</span></span>

- [<span data-ttu-id="81593-143">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="81593-143">Configuration file schema for the .NET Framework</span></span>](../index.md)
