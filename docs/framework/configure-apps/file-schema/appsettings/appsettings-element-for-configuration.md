---
title: '&lt;appSettings&gt; element pro &lt;konfigurace&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cb59120d88816ea193bd8588b152d6b848b682d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="edf5d-102">\<appSettings > elementu pro \<konfigurace ></span><span class="sxs-lookup"><span data-stu-id="edf5d-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="edf5d-103">Obsahuje vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="edf5d-103">Contains custom application settings.</span></span> <span data-ttu-id="edf5d-104">Toto je předdefinovaný konfigurační oddíl poskytované rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="edf5d-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="edf5d-105">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="edf5d-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="edf5d-106">&nbsp;&nbsp;**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="edf5d-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="edf5d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edf5d-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="edf5d-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="edf5d-108">Attribute</span></span>

|           | <span data-ttu-id="edf5d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="edf5d-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="edf5d-110">**soubor**</span><span class="sxs-lookup"><span data-stu-id="edf5d-110">**file**</span></span>  | <span data-ttu-id="edf5d-111">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="edf5d-111">Optional attribute.</span></span><br><br><span data-ttu-id="edf5d-112">Určuje relativní cestu k externí soubor obsahující nastavení konfigurace vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="edf5d-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="edf5d-113">Zadaný soubor obsahuje stejný druh nastavení, které jsou určené v  **\<Přidat >**,  **\<odebrat >**, a  **\<clear >** elementy a používá stejný dvojice klíč/hodnota formátovat jako těchto elementů.</span><span class="sxs-lookup"><span data-stu-id="edf5d-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="edf5d-114">Zadaná cesta je relativní vzhledem ke hlavní konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="edf5d-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="edf5d-115">Aplikaci Windows Forms, to je binární složky (například */bin/ladění*), ne však umístění konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="edf5d-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="edf5d-116">Pro aplikace webových formulářů, cesta je relativní vůči kořenovému adresáři aplikace, kde *web.config* se nachází soubor.</span><span class="sxs-lookup"><span data-stu-id="edf5d-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="edf5d-117">Všimněte si, že modul runtime ignoruje atribut, pokud zadaný soubor nelze nalézt.</span><span class="sxs-lookup"><span data-stu-id="edf5d-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="edf5d-118">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="edf5d-118">Parent element</span></span>

|     | <span data-ttu-id="edf5d-119">Popis</span><span class="sxs-lookup"><span data-stu-id="edf5d-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="edf5d-120">**\<Konfigurace >** – Element</span><span class="sxs-lookup"><span data-stu-id="edf5d-120">**\<configuration>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="edf5d-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="edf5d-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="edf5d-122">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="edf5d-122">Child elements</span></span>

|     | <span data-ttu-id="edf5d-123">Popis</span><span class="sxs-lookup"><span data-stu-id="edf5d-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="edf5d-124">**\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="edf5d-124">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="edf5d-125">Přidá vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="edf5d-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="edf5d-126">**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="edf5d-126">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="edf5d-127">Vymaže všechna nastavení dříve definovaném aplikace.</span><span class="sxs-lookup"><span data-stu-id="edf5d-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="edf5d-128">**\<Odebrat >**</span><span class="sxs-lookup"><span data-stu-id="edf5d-128">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="edf5d-129">Odebere nastavení dříve definovaném aplikace.</span><span class="sxs-lookup"><span data-stu-id="edf5d-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="edf5d-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="edf5d-130">Remarks</span></span>

<span data-ttu-id="edf5d-131">**\<AppSettings >** element ukládá informace o konfiguraci vlastní aplikaci, například databázové připojovací řetězce, cesty k souborům, adresy URL XML webových služeb nebo jiných vlastní konfigurační informace pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="edf5d-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="edf5d-132">Páry klíč – hodnota zadaná v  **\<appSettings >** element probíhal v kódu pomocí <xref:System.Configuration.ConfigurationSettings> – třída.</span><span class="sxs-lookup"><span data-stu-id="edf5d-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="edf5d-133">Můžete použít **soubor** atribut  **\<appSettings >** element *Web.config* a konfigurační soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="edf5d-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="edf5d-134">Tento atribut určuje konfigurační soubor, který poskytuje další nastavení nebo přepíše nastavení zadaná  **\<appSettings >** element.</span><span class="sxs-lookup"><span data-stu-id="edf5d-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="edf5d-135">**Souboru** atribut lze použít v týmu vývoj scénářích správy zdrojového kódu, například když uživatel chce pro přepsání nastavení projektu zadané v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="edf5d-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="edf5d-136">Konfigurační soubory určeného **soubor** kořenový uzel musí mít atribut  **\<appSettings >** místo  **\<konfigurace >**.</span><span class="sxs-lookup"><span data-stu-id="edf5d-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="edf5d-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="edf5d-137">Example</span></span>

<span data-ttu-id="edf5d-138">Následující příklad ukazuje soubor s nastavením externí aplikaci (*custom.config*), který definuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="edf5d-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="edf5d-139">Následující příklad ukazuje konfigurační soubor aplikace, která načítá nastavení v souboru externích nastavení a nastaví vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="edf5d-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="edf5d-140">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="edf5d-140">Configuration file</span></span>

<span data-ttu-id="edf5d-141">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="edf5d-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="edf5d-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="edf5d-142">See also</span></span>

[<span data-ttu-id="edf5d-143">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="edf5d-143">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
