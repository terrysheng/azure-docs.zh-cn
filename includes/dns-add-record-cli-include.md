#### <a name="create-an-a-record-set-with-single-record"></a>创建一个包含一条记录的 A 记录集

若要创建记录集，请使用 `azure network dns record-set create`。 指定资源组、区域名称、记录集相对名称、记录类型和存活时间 (TTL)。

```azurecli
    azure network dns record-set create myresourcegroup  contoso.com "test-a"  A --ttl 300
```

创建 A 记录集后，利用 `azure network dns record-set add-record`将 IPv4 地址添加到该地址集中。

```azurecli
    azure network dns record-set add-record myresourcegroup contoso.com "test-a" A -a 192.168.1.1
```

#### <a name="create-an-aaaa-record-set-with-a-single-record"></a>创建一个包含一条记录的 AAAA 记录集

```azurecli
    azure network dns record-set create myresourcegroup contoso.com "test-aaaa" AAAA --ttl 300

    azure network dns record-set add-record myresourcegroup contoso.com "test-aaaa" AAAA -b "2607:f8b0:4009:1803::1005"
```

#### <a name="create-a-cname-record-set-with-a-single-record"></a>创建一个包含一条记录的 CNAME 记录集

CNAME 记录只允许单个字符串值。

```azurecli
    azure network dns record-set create -g myresourcegroup contoso.com  "test-cname" CNAME --ttl 300

    azure network dns record-set add-record  myresourcegroup contoso.com  test-cname CNAME -c "www.contoso.com"
```

#### <a name="create-an-mx-record-set-with-a-single-record"></a>创建一个包含一条记录的 MX 记录集

在此示例中，使用记录集名称 "@" 在区域顶端（在本例中为“contoso.com”）创建 MX 记录。 这常用于 MX 记录。

```azurecli
    azure network dns record-set create myresourcegroup contoso.com  "@"  MX --ttl 300

    azure network dns record-set add-record -g myresourcegroup contoso.com  "@" MX -e "mail.contoso.com" -f 5
```

#### <a name="create-an-ns-record-set-with-a-single-record"></a>创建一个包含一条记录的 NS 记录集

```azurecli
    azure network dns record-set create myresourcegroup contoso.com test-ns  NS --ttl 300

    azure network dns record-set add-record myresourcegroup  contoso.com  "test-ns" NS -d "ns1.contoso.com"
```

#### <a name="create-a-ptr-record-set-with-a-single-record"></a>创建一个包含一条记录的 PTR 记录集

在此例中，“my-arpa-zone.com”表示代表你的 IP 范围的 ARPA 区域。  此区域中的每个 PTR 记录集对应于此 IP 范围内的一个 IP 地址。

```azurecli
    azure network dns record-set add-record myresourcegroup my-arpa-zone.com "10" PTR -P "myservice.contoso.com"
```

#### <a name="create-an-srv-record-set-with-a-single-record"></a>创建一个包含一条记录的 SRV 记录集

如果要在区域的根目录中创建一个 SRV 记录，可以在记录名称中指定“_service”和“_protocol”。 无需在记录名称中包含 "@"。

```azurecli
    azure network dns record-set create myresourcegroup contoso.com "_sip._tls" SRV --ttl 300

    azure network dns record-set add-record myresourcegroup contoso.com  "_sip._tls" SRV -p 0 - w 5 -o 8080 -u "sip.contoso.com"
```

#### <a name="create-a-txt-record-set-with-single-record"></a>创建一个包含一条记录的 TXT 记录集

```azurecli
    azure network dns record-set create myresourcegroup contoso.com "test-TXT" TXT --ttl 300

    azure network dns record-set add-record myresourcegroup contoso.com "test-txt" TXT -x "this is a TXT record"
```


<!--HONumber=Nov16_HO2-->


