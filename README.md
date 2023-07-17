# spring-boot-security-3.0

Note : If you are using spring boot 3.1.x version then please do the below code change

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        return http.csrf(AbstractHttpConfigurer::disable)
                .authorizeHttpRequests(auth ->
                        auth.requestMatchers("/product-service/welcome", "/product-service/addNewUser").permitAll()
                                .requestMatchers("/product-service/**")
                                .authenticated()
                )
                .httpBasic(Customizer.withDefaults()).build();
    }
